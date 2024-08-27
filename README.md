# CFD-Simulation
CFD simulation of multiple rigidbodies using OpenFOAM/Moordyn coupling package foamMooring.

I understand Python wrappers in FoamMooring are designed to allow more flexible and dynamic control over the mooring system's behavior during a simulation. These wrappers enable users to interact with MoorDyn's API directly from Python scripts, which can be integrated into an OpenFOAM simulation via FoamMooring. Here's my understanding how it generally works:
1. Integration with MoorDyn
FoamMooring couples OpenFOAM with MoorDyn using the MoorDyn API. The Python wrappers provide an interface to this API, allowing me to control and manipulate the mooring system during a simulation. For example, I can use Python to:
Initialize MoorDyn: Set up the mooring system parameters and initialize it within the OpenFOAM simulation.
Update MoorDyn: Dynamically adjust parameters like mooring line lengths, attachment points, or forces based on the simulation's state at each time step.
Retrieve Data: Extract forces, positions, or other relevant data from the mooring lines and use them for control logic or post-processing.
2. Python Scripting
The Python scripts can be used to implement custom control algorithms, such as PID controllers, which can adjust the behavior of the mooring lines based on real-time feedback from the simulation. The typical workflow might include:
Reading Simulation Data: The script can access data from the OpenFOAM simulation (e.g., positions, velocities, forces) to make decisions.
Calling MoorDyn Functions: The script uses the Python wrapper to call MoorDyn functions and update the state of the mooring system.
Writing Outputs: The script can output data to files or update OpenFOAM fields, influencing the simulation in subsequent steps.
3. Example Workflow
Here's a simplified example of how the Python wrapper might be used in a FoamMooring simulation:
Initialization: A Python script initializes the MoorDyn system, setting up the mooring lines and attaching them to the floating body in the simulation.
Control Loop:
At each time step of the OpenFOAM simulation, the Python script:
Reads the current state of the floating body (position, velocity).
Calculates the required adjustments to the mooring lines (e.g., adjusting lengths to maintain stability).
Uses the Python wrapper to update the mooring line parameters in MoorDyn.
MoorDyn computes the new forces on the mooring lines, which are then applied to the floating body in the OpenFOAM simulation.
Data Extraction: After the simulation, the script might extract and analyze the mooring forces and positions to assess performance.
4. Advantages
Real-Time Control: You can implement custom control strategies that dynamically adjust the mooring lines during the simulation.
Flexibility: Python's ease of use and powerful libraries make it suitable for complex tasks like optimization, data analysis, or machine learning-based control.
Integration: The wrapper seamlessly integrates with the overall OpenFOAM simulation, allowing for detailed and customized simulations.
5. Practical Considerations
When using the Python wrappers, you'll need to ensure that:
Performance: The overhead introduced by Python is minimal, especially in time-critical applications.
Error Handling: Proper checks are in place to handle any issues that arise during the script's execution, ensuring that the simulation remains stable.
Synchronization: The script must be well-synchronized with the OpenFOAM time steps to avoid inconsistencies.
The link to my GitHub directory is below, I uploaded my case for moving vessel with pendulum and also my python script I am trying to use to control my vessel direction and speed. The current problem i am having is that I'm getting inaccurate results which symbolise instability in my simulation.  

# Vacuum Cleaner problem
# Aim
To write the python program for Vacuum Cleaner problem
# Program
    agent_table = {
    ('Clean', 'A'): 'MoveRight',
    ('Clean', 'B'): 'MoveLeft',
    ('Dirty', 'A'): 'Suck',
    ('Dirty', 'B'): 'Suck',
    }

    class VacuumCleaner:
    def __init__(self, location='A', status='Clean'):
        self.location = location
        self.status = status

    def percept(self):
        return self.status

    def act(self, action):
        if action == 'MoveRight':
            self.location = 'B'
        elif action == 'MoveLeft':
            self.location = 'A'
        elif action == 'Suck':
            self.status = 'Clean'

    def table_driven_agent(percept):
    return agent_table.get(percept, 'NoOp')

     if __name__ == "__main__":
    vacuum = VacuumCleaner()

    for _ in range(5):  # Run for 5 time steps
        current_percept = vacuum.percept()
        action = table_driven_agent((current_percept, vacuum.location))
        print(f"Percept: {current_percept}, Action: {action}")

        if action != 'NoOp':
            vacuum.act(action)

        print(f"Location: {vacuum.location}, Status: {vacuum.status}\n")
# Output

Percept: Clean, Action: MoveRight
Location: B, Status: Clean

Percept: Clean, Action: MoveLeft
Location: A, Status: Clean

Percept: Clean, Action: MoveRight
Location: B, Status: Clean

Percept: Clean, Action: MoveLeft
Location: A, Status: Clean

Percept: Clean, Action: MoveRight
Location: B, Status: Clean

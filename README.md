The requirements are given at high level, so I have to go ahead with some assumptions on the requirement. My assumptions on this requirement and the setup are given below. And the solution is designed in accordance with the below use cases. This solution can be easily scaled with minimal effort.
1)	Mailbox contains a Microcontroller to operate the door and a Board to communicate with the Android App.
2)	The door operation and the communication between the Microcontroller and board are not in the current scope.
3)	The Board communicates with the Android phone with BLE and with Azure Cloud over HTTPS.
4)	User wants to Lock or Unlock the Mailbox with An Android app which is connected to the board through BLE.
5)	Android App communicates with Azure over HTTPS.
6)	Board sends a notification to the Cloud if there is any new mail in the box. 
7)	Cloud sends notification to the Android App on the same and maintains the mails history in the database.
8)	Cloud exposes On Demand APIs so that the device can query to check on the new mails anytime.
9)	User can reset the Mails count with the App when the mailbox is emptied. 


The solution is architected by respecting the below important SW design guidelines. 
1) Scalability : Can add new features easily, the impact on the existing features is minimal.
2) Reusability : Both the BT Service and UI request handler implementations are hidden behind the interfaces, so they can be easily replacable if the remote BLE device implementation is changed OR the board itself is changed. Rest all other components can be reused.
3)Testability : View updates, Event handling and Model are separated into different components, so unit testing of each module would be hassle-free.

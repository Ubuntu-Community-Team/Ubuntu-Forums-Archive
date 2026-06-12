---
title: "Mouse and keyboard logger"
date: 2013-11-24
forum: General Help
---

### Post by Gopal_Sharma on 2013-11-24
[FONT=arial]Hello,[/FONT]

[FONT=arial]I am writing a application program to log all mouse and keyboard events.[/FONT]
[FONT=arial]For this I read directly device file for mouse and keyboard ([COLOR=#ff0000]/dev/input/...[/COLOR]). It works fine but I have to also log mouse and keyboard events incoming from networks devices.[/FONT]

[FONT=arial]I am sorry! My English is weak.[/FONT]

[FONT=arial]I was saying that logger should also log events when my Linux system being accessed using some remote protocols like RFB etc. My logger is not logging events when I am accessing it using TightVNC application for accessing remotely to a Linux machine or any other application for accessing a Linux machine remotely.[/FONT]

[FONT=arial]Also I have used [COLOR=#ff0000]X11 library[/COLOR] to solve this problem but it is not working. It is logging events to a specific client (application) only after creating a window.[/FONT]

[FONT=arial]Then I made a detail study of X11 library. I have studied that It works on client-server based.[/FONT]

[FONT=arial]X server has a master queue to store events. Every application is treated as a client and each client has its own event queue. Server and client communicate through a some protocol. Server sends events to respective client and client reads events from its event queue.[/FONT]

[FONT=arial]Now what I understand that to log events of all clients, I have to read directly X servers events queue.[/FONT]

[FONT=arial]Could you please help me to solve this problem.[/FONT]

[FONT=arial]Please let me know if I have made any mistake in understanding X11 concepts.[/FONT]

[FONT=arial]Also let me know if there is any other ways to solve this problem.[/FONT]

[FONT=arial]Thanks,[/FONT]
1
[FONT=arial]Gopal Sharma[/FONT]

---

### Post by Gopal_Sharma on 2013-11-24
[FONT=arial][COLOR=#000000].................[/COLOR][/FONT]

---

### Post by The Cog on 2013-11-24
Threads merged and moved to General Help. 
Please don't multipost in different forums.

---


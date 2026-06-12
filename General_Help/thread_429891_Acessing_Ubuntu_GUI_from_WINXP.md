---
title: "Acessing Ubuntu GUI from WINXP"
date: 2007-05-01
forum: General Help
---

### Post by scottnadeau on 2007-05-01
Hi all,
I am trying to find a software package that will allow me to connect to my Ubuntu box remotely from a WINXP machine with a GUI.  Somebody turned me on to Refletions X, but I have been unable to get it to work.  Is this possible to do?

The reason I want to do this is twofold - 1) I'm too lazy to run down to the cold basement every time I want to do something from the console (run Oracle Universal Installer in this case).  2) It seems like cool technology and I want to see if it can be done.

Any thought?
Thanks,
Scott Nadeau
Concord, NH

---

### Post by chrisccoulson on 2007-05-01
Apparently Cygwin allows you to display applications across SSH on your Windows machine. If you're after a full gui, maybe you should use a VNC client. Maybe you could try something like UltraVNC on the Windows machine: [http://www.uvnc.com/index.html]("http://www.uvnc.com/index.html")

---

### Post by Tomosaur on 2007-05-01
> **chrisccoulson said:**
> Maybe you could try something like UltraVNC on the Windows machine: [http://www.uvnc.com/index.html]("http://www.uvnc.com/index.html")

If you download [Cygwin/X](http://x.cygwin.com/) for Windows, and set up your Ubuntu box to be an SSH server, you should be able to log in via SSH (with X enabled) from Windows, and run programs on your Ubuntu box. The GUI of these programs should show up on your Windows desktop. The desktop of your Ubuntu box, however (panels etc) will not show.

---


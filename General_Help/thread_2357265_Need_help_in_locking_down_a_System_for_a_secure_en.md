---
title: "Need help in locking down a System for a secure environment."
date: 2017-03-31
forum: General Help
---

### Post by robert71 on 2017-03-31
Hi Guys, 

I have been recently tasked with preparing a system for a environment with high security. 

Usually I would use GPO's but one of the main requirements is that the system cannot be a member of a domain. 

So I believe that Ubuntu is my best option my requirements are as follows: 

Upon logging in the system must launch a web browser and **allow access to one site only**: [www.example.com]("http://www.example.com") 
(users should not be able to brows to any other site or should be redirected to one site)

Users should not be able to close the browser and gain access to the OS.  (I'm guessing this means that the windows key etc should not bring up the ubuntu launcher etc..)

Access to all physical external ports should be disabled e.g. usb. 

Does anyone know how to accomplish these requirements using Ubuntu or can point me to tutorials manuals etc.. 

Any help is appreciated>

---

### Post by oldfred on 2017-04-01
I do not know about your requirements, but sounds like Kiosk mode.

And with many new UEFI systems with Secure Boot, you can turn off USB boot.

Most of this is now older, you may want to search for newer info.
Kiosk discussions:
[http://ubuntuforums.org/showthread.php?t=2113023](http://ubuntuforums.org/showthread.php?t=2113023)
[http://ubuntuforums.org/showthread.php?t=1872560](http://ubuntuforums.org/showthread.php?t=1872560)
[http://ubuntuforums.org/showthread.php?t=1881141](http://ubuntuforums.org/showthread.php?t=1881141)
[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)
[http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/)
chromium kiosk using Tiny Core Linux. Talk about small and light!
[http://ubuntuforums.org/showthread.php?t=1891594](http://ubuntuforums.org/showthread.php?t=1891594)
[http://spins.fedoraproject.org/kiosk/#home](http://spins.fedoraproject.org/kiosk/#home)

---


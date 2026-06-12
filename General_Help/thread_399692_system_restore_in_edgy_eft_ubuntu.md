---
title: "system restore in edgy eft ubuntu"
date: 2007-04-02
forum: General Help
---

### Post by numerical on 2007-04-02
Is there a feature similiar to systme restore (like in windows) in edgy ubuntu 6.10? after installing many network programs (16 different ones ) in an attempt to connect to my wireless router,I guess there was a conflict so i uninstalled the other network programs but still my default networking app doesnt open .Ever since I made these changes my system is very unstable (keep getting bug error when i try to open networking. (hence i cant connect to the internet to fix the problem) .Is system restore an option or should i reinstall ubuntu over a newly formatted partition?  ( if someone could tell me how to fix network manager (maybe uninstall adn reinstall?) then I wont have to reformatt adn reinstall the whole ubuntu.

Thanks everyone!

---

### Post by kidders on 2007-04-02
Hi there,

To be honest, reinstalling Linux is something you should only ever need to do if your system is completely and utterly crippled, or has been compromised. I'm not a wireless expert (so I may not be much help getting you set up if you're configuration is in any way odd), but I should at least be able to help you get back to square one!

If I had your problem, I would...

[LIST]
[*]Remove everything WLAN-related that I'd installed.
[*]Check /etc for any old settings that may have survived the removal. (Linux is often reluctant to delete application settings, especially if they've been altered.)
[*]Check running processes for anything suspicious that could be related to wireless networking, and terminate them.
[*]Deactivate wireless interfaces & remove references to them from /etc/network.
[*]Remove any kernel loaded modules that seem like they might be drivers for your hardware.
[/LIST]

Since you've had trouble before, I would suggest finding a HOWTO for a Linux distro that is at least *similar* to Ubuntu, describing what to do exclusively in terms of a terminal interface. That way, you'll be able to gain a clearer insight into what's going on underneath the UI, and any error messages should be clearly visible, or very easily accessible. In the event something goes pear-shaped again, other Ubuntuers will be able to give you very precise help, based specifically on how far you get, and precisely what's gone wrong.

---

### Post by numerical on 2007-04-03
Thanks for your time.I ve tried my best to do what you suggested and i didnt find anything running in processes and i cannot remove some programs  in synaptic because i get an error message saying "first you must fix broken files ".The main problem preventing me from connecting to the INTERNET is when I open NETWORKING I keep getting the same bug report {doesnt detect any  "known" bugs} whenever i try to open NETWORKING. That seems to be the problem. otherwise when i open Network tools it detects the router and correct IP adresses etc..correctly , however when i try to configure the device it says i dont have permission to do that . Any other suggestions at this stage.
thanks for your time .
Numbers

---


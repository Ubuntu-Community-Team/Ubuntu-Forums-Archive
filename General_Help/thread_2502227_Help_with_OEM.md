---
title: "Help with OEM"
date: 2024-11-06
forum: General Help
---

### Post by rickiespence on 2024-11-06
Hello,
I have actually installed ubuntu using oem installation for a client, but now my office is asking to make more additional changes to it. Is it possible to switch back to the same OEM again and add some changes and ship the end user? Please help me with this.
[COLOR=#000000][FONT=Arial][[size=1][color=#f8f8f8]slope game[/color][/size]](https://slope3.com)[/FONT][/COLOR]

---

### Post by grahammechanical on 2024-11-06
I do not understand what you are asking. Some years ago I experimented with Ubuntu OEM installs as a way of testing Ubuntu. I also purchased a couple of years ago a laptop that had an OEM install of Ubuntu 20.04 LTS on it.

At my first boot I was invited to put in a user name and a password. After that I had complete ownership of the OS. I was the only user. The supplier did not retain a username or password that would give their engineers access to the operating system on what was now my machine.

So, I do not understand what you mean by this question:

> s it possible to switch back to the same OEM again and add some changes and ship the end user? Please help me with this.

If you are using a standard Ubuntu ISO image to create that OEM installation then it will be a standard version of Ubuntu that will be on the machine. If you are using a modified Ubuntu ISO image with specialised hardware drivers and/or changes to the default software applications, then just go through the process that was used to create that modified Ubuntu ISO image.

My supplier used a modified Ubuntu ISO image that contained special keyboard drivers to give full functuality to the keyboard. And a set of wallpapers and well as adding the supplier software repository to the software sources.list file.

Ubuntu 24.04 LTS has an option for Autoinstall. Perhaps you are thinking of that. I am a home user I do not have an autoinstall yaml document. This is something that I have not tried even out of curiosity. I have never selected that option.

[https://canonical-subiquity.readthedocs-hosted.com/en/latest/reference/autoinstall-reference.html](https://canonical-subiquity.readthedocs-hosted.com/en/latest/reference/autoinstall-reference.html)
 
My one disappointment with my OEM supplier was the lack of a user manual for the hardware and the OS. Does your organisation provide even a set of startup instructions? I wonder.

Regards

---


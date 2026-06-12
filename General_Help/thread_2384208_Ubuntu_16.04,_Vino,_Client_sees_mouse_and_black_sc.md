---
title: "Ubuntu 16.04, Vino, Client sees mouse and black screen"
date: 2018-02-03
forum: General Help
---

### Post by quadphile on 2018-02-03
The setup is as follows:
-Ubuntu VM running within host ( VM recently "apt upgrade"d)
-Trying to use built in Vino for same UX as a real computer
-Connect to Vino from OSX using screen sharing, I know about turning off the encryption setting that prevents OSX Screen Sharing from connecting

The problem, to which I have spent an excessive amount of time on is that the OSX VNC client doesn't see the GUI, it's a black screen with a mouse that functions, so I'm connected to Vino successfully since the mouse works (I can see on the VM host's terminal that the control is occurring).  I've tried removing Vino, tried using other VNC servers, I've tried watching the vino-server console output to no insight.  I've tried from the VM host using Remina and it also has a black screen.

It used to work, had a lumpy auto upgrade and I don't know what broke.  ("Don't know what broke and now spending the weekend fixing something that used to work" is why I ditched Microsoft by the way...I could cry).  Since it doesn't work, I'm now scared to update anything else.

I just want Vino completely removed and to start over, assuming that the issue here is an obscure config file somewhere, apt-get remove followed by apt-get install leaves me stuck with the same problem.

Thanks for the help,

---


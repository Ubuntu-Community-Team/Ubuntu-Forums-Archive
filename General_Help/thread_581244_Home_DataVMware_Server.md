---
title: "Home Data/VMware Server"
date: 2007-10-19
forum: General Help
---

### Post by mahousaru on 2007-10-19
I'm planning on moving my home server off from OpenSuSE 10.3 over to Gutsy just so I only have one distro at home.  The main uses of the box is to run samba, AMP and VMware.  I've always used SuSE until recently, but I've been won over :)

The box it self is quite beefy and even though normally it doesn't have gnome loaded, I have found myself sitting more and more at the desktop using a virtual machine for some purpose.  So basically the question is should I go for the server edition or for the desktop edition?  

If I install the server edition and then add gnome will it install all the other cr... useful applications that I won't need on a server?  

Any advice on the advantages of the server edition would be much appreciated

Many thanks!

---

### Post by thirddeep on 2007-10-19
You can take debian/ubuntu and at any time add X / Gnome / KDE / ....

But yes, installing the base set of Gnome will install a bunch of other applications/utilities that is not required on a server.

Since you have WMware on, why not install a desktop image and keep the server clean ?

Thd.

---

### Post by mahousaru on 2007-10-19
....

Oh I didn't think of that :p

Can vmware-console run from cli without a gui installed?

*scurries off to do some reading*

---

### Post by thirddeep on 2007-10-19
For VMware server, the GUI is a separate package.  I run it on one machine to control others....

I have not looked at full command line controls for VMware.  I have a feeling Xen is better on that side.

Thd.

---

### Post by mahousaru on 2007-10-19
Ah I get where you are coming from.  I normally work from my living room over the network, but recently I've been squatting in the cubby hole and running vmware-console from the box itself. So I have been actually running in gnome a lot.  I have gnome installed with OpenSuSE (with 100's of un-needed apps :p), but I normally have it defaulting to init 3.

Does the server install do anything special apart from strip out the GUI?  I think that this the most wonderful approach to server builds, as I normally spend hours hacking out all the *beep* from an OES Linux install.

Many thanks for your input Thd!

---


---
title: "Switching to Kubuntu"
date: 2005-10-24
forum: General Help
---

### Post by JohnGalt on 2005-10-24
I had installed ubuntu because I had never used gnome before. I then installed the kubuntu-desktop and it worked ok. Problem is that gnome kept hanging up on me, wouldn't let me log out without freezing, and was taking up too much ram. I saw on the forum where it said you could uninstall gnome and use it as kubuntu with the kubuntu-desktop. What differnce is there between installing kubuntu and installing ubuntu and using the kde desktop? Well, after uninstalling gnome packages the computer froze and restarted to a prompt only. I did the apt-get install kubuntu-desktop. Now it is not working right. I can't bring up konsole along with several of the other utilities. I only have the ubuntu install disc and no more blanks to burn the kubuntu. Is it possible to install it from a second hard drive? or is there some other way to fix my problem?
Thank you for your help

---

### Post by brentoboy on 2005-10-24
sounds like you ar missing parts of kde try this...

sudo apt-get install kde kdm

maybe that will get you back on your feet

---

### Post by ecobuntu on 2005-10-24
Can you log into gnome at all?  If you need to reinstall you'll have to install Ubuntu then at the terminal type:
sudo apt-get install kubuntu-desktop

I've had those same issues with gnome hanging when i try to log out.  i've filed a bug report already.

---

### Post by JohnGalt on 2005-10-24
gnome is completely gone as far as I can tell. I want to use just kubuntu so I don't have those gnome programs hanging around. I did the install kde and it added more stuff but terminal still wont open. I don't want to install ubuntu, just kubuntu. anyway to do it from a second hard drive instead of burning a disk?

---

### Post by stuporglue on 2005-10-24
One the computer starts up completely, hit ctrl+alt+F2 and log in there. 

Once there do update

sudo apt-get update 

and upgrade

sudo apt-get upgrade

and try to install kubuntu-desktop again

sudo apt-get install kubuntu-desktop

If that doesn't work, please type in the output here...at least the important looking parts (ie. where it says "error" etc.). It'll make it easier to figgure out what's wrong.

---

### Post by JohnGalt on 2005-10-24
As far as I can tell, there is no error. It just doesn't work right. I still can't bring up terminal. Is there anyway to do a clean install of kubuntu by using the iso on another hard drive without burning it? I have the ubuntu disk but I don't want to install gnome at all.

---


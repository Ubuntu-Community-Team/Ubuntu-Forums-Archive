---
title: "Ubuntu and Kubuntu"
date: 2007-05-10
forum: General Help
---

### Post by jazzenator on 2007-05-10
Hello guys and gals

I am new to the linux scene coming from a 10 year background of windows and 2 year of Mac.
I was attracted to linux just for the hell of it and the fact that Mac OS X shares a lot of linux architecture. 

So here I doff my hat and say a big hello to all.

Anyway, to keep it short. I took my old laptop. Erased all traces pf windows and installed Ubuntu on it. It is good however, I like thr Kubuntu desktop. Is it possible to install Ubuntu and Kubuntu on the same machine on the same drive and just switch between the two on start up? Will I be able to access my same folders and files from both of the desktops?

Let me know. 

Thanks 

Jazz

---

### Post by taurus on 2007-05-10
Yes.  You can have both Gnome and KDE on the same machine using the same account.  Just pick which window manager you want to use from the Options (bottom left corner) at the GUI login screen.  

If you installed Kubuntu version, then you can install Gnome with

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by johnnymac on 2007-05-10
Actually, If you install Ubuntu, and then install the KDE Libraries....then that's it.  I myself like XFCE, but I like having everything where I want like in Ubuntu....options are for me to install Xubuntu; however, I just install Ubuntu and then the XFCE libraries....that matches my liking.

---

### Post by TheWizzard on 2007-05-10
yes you can use both kde and gnome. but i'd advice you to use different home directories because some programmes may get messed up .

---

### Post by taurus on 2007-05-10
> **TheWizzard said:**
> yes you can use both kde and gnome. but i'd advice you to use different home directories because some programmes may get messed up .

I think you are confused between having both Ubuntu & Kubuntu on the same machine with installing two different Linux distros on the same machine.

---

### Post by amicitas on 2007-05-10
Here are some links with instructions on this.  

[Installing Gnome on Kubuntu]("http://www.psychocats.net/ubuntu/gnome")
[Installing KDE on Ubuntu]("http://www.psychocats.net/ubuntu/kde")

You can do these updates through your package manager as well (synaptic or adept).  While it is doing the install you will need to expand the pane that gives you more details so that you can tell the installer which login screen to use.


amicitas

---

### Post by TheWizzard on 2007-05-10
> **taurus said:**
> I think you are confused between having both Ubuntu & Kubuntu on the same machine with installing two different Linux distros on the same machine.

no i'm not. i'm talking about installing ubuntu and then aptitude install kubuntu-desktop (or alternative ways to install kde). 
some apps seem to behave differently in gnome and kde. and switching between the two messes stuff up. this is from my own experience. 
if i'm not mistaken there is some advice on this issue on aysiu's website. 

cheers

---

### Post by jazzenator on 2007-05-10
> **johnnymac said:**
> Actually, If you install Ubuntu, and then install the KDE Libraries....then that's it.  I myself like XFCE, but I like having everything where I want like in Ubuntu....options are for me to install Xubuntu; however, I just install Ubuntu and then the XFCE libraries....that matches my liking.

Thanks for the reply. I have installed Ubuntu and would like to add Kubuntu. How do I go about adding this to the install, bearing in mind that I am a  linux newb.
My ideal dream setup would be having both desktops and being able to choose which to boot into on starting the machine up. Accessing all my files from the same directory. Can someone advise on how to do that please?

Thanks once again.

---

### Post by jazzenator on 2007-05-10
> **amicitas said:**
> Here are some links with instructions on this.  

[Installing Gnome on Kubuntu]("http://www.psychocats.net/ubuntu/gnome")
[Installing KDE on Ubuntu]("http://www.psychocats.net/ubuntu/kde")

You can do these updates through your package manager as well (synaptic or adept).  While it is doing the install you will need to expand the pane that gives you more details so that you can tell the installer which login screen to use.


amicitas


Thanks I will give it a bash tomorrow and let you'll folks know. Regards for now.

---

### Post by strabes on 2007-05-10
When you install ubuntu-desktop, it's most likely going to change your bootsplash from the kubuntu one to the default ubuntu one. If you want to change it back, you can run the following command and then press the number of the bootsplash you want to use.

```
    sudo update-alternatives &#8211;config usplash-artwork.so
```

You should also run

```
    sudo dpkg-reconfigure linux-image-`uname -r`
```

to write the settings into your /boot/grub/menu.lst file.

When you restart your computer, the bootsplash should be the one that you want.

If you want to completely remove the alternative bootsplash that comes with kubuntu & xubuntu and restore the original ubuntu one, run this command in a terminal:

```
sudo aptitude remove kubuntu-artwork-usplash xubuntu-artwork-usplash && sudo aptitude install usplash-theme-ubuntu
```

---


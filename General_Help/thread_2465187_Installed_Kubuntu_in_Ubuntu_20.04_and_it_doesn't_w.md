---
title: "Installed Kubuntu in Ubuntu 20.04 and it doesn't work"
date: 2021-07-24
forum: General Help
---

### Post by dora5 on 2021-07-24
I just upgraded from Ubuntu 18.04 to Ubuntu 20.04.   The result is ugly.

So I then installed Kubuntu desktop by using sudo apt-get install kubuntu-desktop.

It went through a great long thing and clearly installed Kubuntu desktop or atleast a lot of desktop features, and then set up grub.   

Then I rebooted.  Grub didn't give Kubuntu as an option.  It said it booted into Kubuntu.   But it then presented me with the plain old Ubuntu desktop - though it is using some Kubuntu software like Dolphin by default.  And NO options to set up Kubuntu appearance are there.

Also no options to use a different desktop on the login page - anywhere, let alone an icon that gives me choices next to my name.  And it now tells me I'm in Ubuntu on the login screen, not Kubuntu.

In package manager it says kubuntu-desktop is installed.

How do I get it to ACTUALLY DO KUBUNTU?

---

### Post by GhX6GZMB on 2021-07-24
You should move this to the "New to Ubuntu" section.
You're in over your head here, and apparently regard Kubuntu as an app for Ubuntu.

If you want to go to Kubuntu, the way is to do a live boot plus install from a DVD/USB. Anything else means: trouble.

---

### Post by monkeybrain20122 on 2021-07-24
> **dora5 said:**
> I just upgraded from Ubuntu 18.04 to Ubuntu 20.04.   The result is ugly.


How so? 18.04 and 20.04 don't look that much different, maybe it is because of old config files that got left over from 'upgrade'. For that and other reasons I never do "upgrade" but a clean install.


> 
So I then installed Kubuntu desktop by using sudo apt-get install kubuntu-desktop


Bad idea. Aside from duplicating a lot of packages which do essentially the same thing (ark and file roller, kate and gedit, dolphin and nautilus, okular and evince, discover and gnome-software  .. etc etc) and clogging up your hard drive you may mess up your system as different configurations live in the same system. If you want a different DE always choose something similar like gnome, gnome classic, unity or (?) mate, not something massively different like kde. I would just backup my data and install kubuntu from scratch if kde plasma is what you want.

---

### Post by tea for one on 2021-07-24
> **dora5 said:**
> How do I get it to ACTUALLY DO KUBUNTU?

After you have selected your user name at the log-in screen, there is a little gear icon in the bottom right corner.
Click this icon to select your Desktop session and then enter your password.

However, as [COLOR="#0000FF"]ml9104[/COLOR] and [COLOR="#0000FF"]monkeybrain20122[/COLOR] have mentioned, you have created a bit of a hybrid system, which will inevitably give you a headache in the future.

I would take their advice, back up, install Kubuntu from scratch and restore your data.

---

### Post by guiverc on 2021-07-24
I'm a lover of multiple desktop environments.

The system I'm replying to you on currently has 3 installed.

I select at login which I want to use for that session, which is exactly what @tea for one suggested.

You can have either Kubuntu or Ubuntu's `plymouth` screen, but cannot use both. You can use the Ubuntu (`gdm3`) or Kubuntu (`sddm`) greeter but not both - so your system will not say Ubuntu/Kubuntu ... what I noted is called a *hybird* system in prior posts; but it's a system you control.  .. *I can repeat this for many like things.. but you'll hopefully have got the idea*

There are costs to having multiple desktops though; so if you're a newbie it's probably not recommended. Beyond the added size on disk, larger updates (both desktops & packages will be updated) etc, your menus are also more complex and you risk using different applications that don't match your desktop which can waste system resources, which may or may not matter depending on how powerful your machine.

Me as stated, I love it, however the system will not appear as polished and issues make it less than ideal for newbies I'll admit.

---


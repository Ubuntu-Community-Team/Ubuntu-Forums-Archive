---
title: "Help haha"
date: 2015-10-14
forum: General Help
---

### Post by mick18 on 2015-10-14
Hello Folks as im new to ubuntu i have a question with regards to ubuntu.when i start my pc ubuntu starts but says there an error but then just carrys on as normal.I believe the errors are due to me being stupid and installing half installing and generally messing things up.is there a program that scans ubuntu for errors and allows me to remove things that i havent installed properly as i have forgotten what half of them were.An example is i installed music player daemon but could never get it to work and thought i have removed it but its still showing in the task bar.

kind regards 

mick

---

### Post by howefield on 2015-10-14
Does the error look something like the attached image(s) ?

---

### Post by grahammechanical on 2015-10-14
Ubuntu has a utility that detect crashes. That is what gave you that error message. It is called Apport. It will also collect information that could be useful for fixing the problem (bug) but this part of Apport is disabled by default in released versions of Ubuntu because the logs it collects to send to the Ubuntu developers with the report of the bug could contain confidential information.

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

Fixing things is never easy. I doubt very much if it can be automated. Might cause more breakages. There are some commands that can be run.

To fix broken packages

```
sudo apt-get -f install
```

To fix broken packages by removing them if necessary

```
sudo apt-get -f remove
```

Some of us install Synaptic Package Manager. That has a GUI and we can do things with it like, mark a package for removal, mark a package complete removal, mark a package reinstall and well as installing packages. It will give us a list of what other packages are going to be removed as well. They are called dependencies (depends).

It is preferable to install and remove applications by using the software centre. We can do it otherwise but we need to keep in mind that sometimes the quick and easy way to fix things is to reinstall the OS. Often that is the best way.

Regards.

---

### Post by mick18 on 2015-10-14
> **howefield said:**
> Does the error look something like the attached image(s) ?


Yes exactly like that

---

### Post by mick18 on 2015-10-14
so if i always use software centre i should never get any problems.seems silly to have to keep reinstalling os  and a pain in the ass

---

### Post by deadflowr on 2015-10-14
> **mick18 said:**
> so if i always use software centre i should never get any problems.seems silly to have to keep reinstalling os  and a pain in the ass
No, you'll most likely have fewer problems, but installing everything from the software center doesn't guarantee no problems.

As far reinstalling, it's a nuclear option. But a quick one.
I've routinely found a reinstall of Ubuntu is actually quicker to do than trying to install some programs on Windows.

After a while though, you'll understand how software packaging and installation works on Ubuntu and a reinstall will more and more likely never be necessary.

---

### Post by mick18 on 2015-10-14
> **deadflowr said:**
> No, you'll most likely have fewer problems, but installing everything from the software center doesn't guarantee no problems.

As far reinstalling, it's a nuclear option. But a quick one.
I've routinely found a reinstall of Ubuntu is actually quicker to do than trying to install some programs on Windows.

After a while though, you'll understand how software packaging and installation works on Ubuntu and a reinstall will more and more likely never be necessary.

Ok thank you very much

---

### Post by Bucky Ball on 2015-10-14
This looks like the old apport issue. It is a bug tracker that is used during OS development and, for some reason, wasn't switched off in the release (at least that's what I've read). To do that, open a terminal and paste these commands in:

```
sudo nano /etc/default/apport
```

A file editor is now open. Change enabled from "0" to a "1" so it looks like this:

```
enabled=1    
```

To turn it off make it:

```
enabled=0
```

Answer from [here]("http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport"). 

Hit control+x then 'y' to save and exit, then reboot and see what happens after you have made the changes.

I have had this issue and used this fix on numerous installs. And +1 to most of what is said above. Once you become more familiar with Linux you will rarely need to reinstall from scratch. We all need to upgrade when our release is no longer supported (or preferably before it gets to that) but that can be done, usually, online and inside the install without having to wipe and start again. :)

---

### Post by mick18 on 2015-10-14
will try this now.Its just little things that are anoying like everytime i log in i have to use nvidia x server to change desktop size so its fits my  tv but i can live with it.thanks for your help

---

### Post by Bucky Ball on 2015-10-14
> **mick18 said:**
> ... everytime i log in i have to use nvidia x server to change desktop size so its fits my  tv ...

That's what we're here for. Post a new thread about this and see how you go. :)

---

### Post by mick18 on 2015-10-14
> **Bucky Ball said:**
> This looks like the old apport issue. It is a bug tracker that is used during OS development and, for some reason, wasn't switched off in the release (at least that's what I've read). To do that, open a terminal and paste these commands in:

```
sudo nano /etc/default/apport
```

A file editor is now open. Change enabled from "0" to a "1" so it looks like this:

```
enabled=1    
```

To turn it off make it:

```
enabled=0
```

Answer from [here]("http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport"). 




Hit control+x then 'y' to save and exit, then reboot and see what happens after you have made the changes.

I have had this issue and used this fix on numerous installs. And +1 to most of what is said above. Once you become more familiar with Linux you will rarely need to reinstall from scratch. We all need to upgrade when our release is no longer supported (or preferably before it gets to that) but that can be done, usually, online and inside the install without having to wipe and start again. :)

This worked a treat after i tried a couple of times,thank you

---

### Post by Bucky Ball on 2015-10-14
All good. :)

Please mark thread as solved. (See first link in my signature, thanks) and try posting a thread about the other issue. Good luck.

---


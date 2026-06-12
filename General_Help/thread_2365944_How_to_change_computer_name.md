---
title: "How to change computer name"
date: 2017-07-12
forum: General Help
---

### Post by Xinghao_Chen on 2017-07-12
In the System Settings -> Details tab window, there is this "Device name" entry. How do I go about changing the name?

The Ubuntu Help (from the tool wheel on top-right) and a search in the forums for "change computer name" did not generate relevant instruction. Hence my asking for help here. Thank you.

---

### Post by Xinghao_Chen on 2017-07-12
Forgot to add that this is in 14.04 install.

---

### Post by #&amp;thj^% on 2017-07-12
You need to edit the computer name in two files:

```
/etc/hostname 
```
and
```
/etc/hosts
```

These will both need administrative access, I would use nano for this propose.

---

### Post by CatKiller on 2017-07-12
It's called the hostname.

It's referenced by both /etc/hostname and /etc/hosts. It certainly used to be the case that you had to open both of them for editing before making changes to either of them, or you would break sudo which, in particular, meant that you couldn't open the other one to un-break sudo.

The System Settings page you refer to appears to allow text entry in the hostname box, but I haven't tried changing it to see if it does anything. If I wanted to change the hostname I would do it by simultaneously editing those two files.

Ninja'd by 1fallen.

---

### Post by Xinghao_Chen on 2017-07-12
On my screen in the Details window, the Device name entry is in grey and I cannot make any change to it.

I opened 2 emacs windows for /etc/hosts and /etc/hostname but neither would allow me to edit. would "sudo emacs" do the trick?

---

### Post by Xinghao_Chen on 2017-07-12
I have just migrated 14.04 from a hdd to a mSATA drive and don't want to do anything to disturb the system. What does "break" and "un-break" sudo mean?

---

### Post by #&amp;thj^% on 2017-07-12
> **Xinghao_Chen said:**
> On my screen in the Details window, the Device name entry is in grey and I cannot make any change to it.

I opened 2 emacs windows for /etc/hosts and /etc/hostname but neither would allow me to edit. would "sudo emacs" do the trick?
```
sudo nano /etc/hosts 
```
And
```
sudo nano /etc/hostname 

```
Will work.

---

### Post by #&amp;thj^% on 2017-07-12
> **Xinghao_Chen said:**
> I have just migrated 14.04 from a hdd to a mSATA drive and don't want to do anything to disturb the system. What does "break" and "un-break" sudo mean?

Using "sudo" grants you permissions to change your system _for either a good change or a bad change_ that will **Break** your system.
So in short a bad command using "sudo"  can Break your system...and also using "sudo" with a Good command can un-Break your system, Providing you have not used code i will not mention or refer to here.

---

### Post by deadflowr on 2017-07-12
You can always run a sed one-liner to change both at once
Example
```
sudo sed -i 's/old-name/new-name/g' /etc/hosts /etc/hostname
```
replace old-name with the current name listed in the files.
replace new-name with whatever the new name will be.

---

### Post by Xinghao_Chen on 2017-07-12
Thank you all for the help.

---

### Post by CatKiller on 2017-07-12
> **deadflowr said:**
> You can always run a sed one-liner to change both at once
Example
```
sudo sed -i 's/old-name/new-name/g' /etc/hosts /etc/hostname
```
replace old-name with the current name listed in the files.
replace new-name with whatever the new name will be.

That is a very good tip. Thank you.

> **Xinghao_Chen said:**
> I have just migrated 14.04 from a hdd to a mSATA drive and don't want to do anything to disturb the system. What does "break" and "un-break" sudo mean?

sudo looks up the hostname as part of the authentication process. If those files differ as to what the name of the host is, the authentication step fails, and so sudo does not work any more until those files agree on what the name of the host is - which you can't fix because sudo doesn't work. It's a hassle of either booting in single-user mode (which makes you root without using sudo), or booting from external media, to change the files if you get in that predicament.

Glad you got it sorted without getting into that pickle, and good work marking the thread as Solved so that other people can find the working solution.

---


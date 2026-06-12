---
title: "2 problem in one thread."
date: 2006-10-26
forum: General Help
---

### Post by sweetthdevil on 2006-10-26
Hi, 

I've a problem my webcam Philips Toucam Pro.

I Install Edgy, last week on a fresh hard drive, but when i was using dapper my webcam was working well. 

So i search the board and install PWC. But it doesn't change. Still no picture in ekiga. 
I then install camorama, but i've got a error  when i open it.
could not connect to video device (/dev/video0)

```
sweetth@sweetth-desktop:~$ camorama
/home/sweetth/.gtkrc-2.0:46: error: unexpected identifier `gnome-panel', expected character `='
```


So if anyone could help me i'll appreciate it a lot. ;) 

Thanks

---

### Post by frodon on 2006-11-07
Run a :
```
sudo apt-get install module-assistant camstream
sudo m-a update,prepare,a-i spca5xx
```Then reboot.
Camstream is a tool which allow you to configure and see if your webcam is working well.
Just type "camstream" in a terminal to launch it.

---

### Post by sweetthdevil on 2006-11-07
Oh sorry but it's now ok.

The pwc driver was broken ( already broken in edgy kernel)

Thanks for your help.

---


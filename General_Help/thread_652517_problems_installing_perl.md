---
title: "problems installing perl"
date: 2007-12-28
forum: General Help
---

### Post by Pizza the Hutt on 2007-12-28
Help!

I accidently uninstalled perl and gnome with it. Now my GUI is gone and I have only the terminal to work with.

If  I do apt-get install -f or apt-get-install perl I get error messages about  a broken pipe and a corrupted tar file and that there is something wrong with dpkg. Tying to reinstall dpkg does not work either.

---

### Post by taurus on 2007-12-28
What happens when you run these two commands from a prompt?

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by Pizza the Hutt on 2007-12-29
When I type 
```
sudo apt-get update
```
it says unable to retrieve package and it does that with a few packages. Maybe it does not recognize my wireless network connection. I will try it on a wired network later.

When I try
```
sudo apt-get install ubuntu-desktop
```
I get a message that tells me about unmet dependencies.

---

### Post by taurus on 2007-12-29
It would be nice if you can post the outputs of both commands when you run them from a terminal.

---

### Post by Pizza the Hutt on 2007-12-29
That is a bit difficult, because I can't cut it from the terminal and paste it somewhere else. I am using a dual boot Windows XP/ Ubuntu Gutsy Gibbon. I have to reboot each time between trying to fix Ubuntu and accessing this forum. I will write it on a piece of paper and type it in.

---

### Post by taurus on 2007-12-29
If your network connection is not working, it's more or less useless to run those two commands since they will try to pull files over from the network.

---

### Post by Pizza the Hutt on 2007-12-29
I am not sure if my network is working under Ubuntu, because the browser is not working. The console is all I can use right now. I have no GUI, which is like being blind.

---

### Post by taurus on 2007-12-29
What happens if you run this command to see if you can get out to the world?

```
ping -c w www.google.com
```
Are you sure you have not tried to see if you can start X server again?

```
startx
```

---

### Post by Pizza the Hutt on 2007-12-30
```
ping -c w www.google.com
```
gives me  an error message 
bad number of packages to transmit.

```
startx 
```gives me an error message

```
/etc/xII/x is not executeable unable to connect
```

My Ubuntu CD is in my apartment and I am traveling with my laptop. I won't get back for another two weeks.

---

### Post by Pizza the Hutt on 2007-12-30
I downloaded perl on my Windows partition and on my jumpdrive. In which path do I find those in the terminal and how do I install it?

---

### Post by taurus on 2007-12-30
It depends on the format of the file that you downloaded and where the jumpdrive is mounted.  Is it mounted right now on your Ubuntu machine?

```
df -h
```

---

### Post by Pizza the Hutt on 2007-12-30
I tried this. It said that the program cf is not installed. When I tried to install cf, it said unmet depencies and it would need perl in order to be installed.

---


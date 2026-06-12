---
title: "Network Problem In Ubuntu Software Center."
date: 2013-04-25
forum: General Help
---

### Post by Ashfaqur Rahman on 2013-04-25
I have an active internet connection.
But ubuntu software center is saying that I have no network connection!!
I cant install any software.
I am using a 3G Modem.

---

### Post by ibjsb4 on 2013-04-25
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

Get any errors?

---

### Post by Ashfaqur Rahman on 2013-04-25
No got no error.

---

### Post by Bashing-om on 2013-04-25
Ashfaqur Rahman; Hi !

On to the next step;
terminal code:
```
sudo apt-get upgrade
```
Post back any errors.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by Ashfaqur Rahman on 2013-04-26
Result:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

@Bashing-om

---

### Post by ibjsb4 on 2013-04-26
You seem to be in good shape.  Try installing something.  If you install method will not work, try this in terminal:

```
sudo apt-get install **NAMEofPACKAGE**
```

And replace name of package with package name.

---

### Post by Ashfaqur Rahman on 2013-04-26
Actually there's nothing wrong with apt-get it works just fine.
Problem with software center. It says that i have no internet connection so i cant install anything from there though i have active internet connection.

---

### Post by Bashing-om on 2013-04-26
Ashfaqur Rahman;

Well, seems that the problem is particular to the Software Center. Might try (re-)configuring it.
```
sudo dpkg-reconfigure software-center
```
Else; consider (re-)installing the software center application ?[INDENT]
just my thought

[/INDENT]

---

### Post by cactus john on 2013-04-26
I'm currently getting the same in the software-updater on the two boxes Im running 13.04 in.
apt-get update working ok
Software updater states to check my internet connection which is on wifi, no problems there..desktop box gives me the same thing and it's cabled to internet.

---

### Post by ibjsb4 on 2013-04-26
You can also try opening it in terminal and see if you get any errors.

```
software-center
```

---

### Post by Bashing-om on 2013-04-26
@ cactus john

Version 13.04 still has some wrinkles to iron out in respect to the GUI updater.
See this link and see if it "might" apply in your situation: Post #27 in particular;
[http://ubuntuforums.org/showthread.php?t=2138987](http://ubuntuforums.org/showthread.php?t=2138987)[INDENT=2]
time solves a lot of things
[/INDENT]

---

### Post by Ashfaqur Rahman on 2013-04-26
Just Found What My Problem Is!!
My problem is same as [B]cactus john .
[/B]
I use 3G Modem to connect to internet. When I connect my 3G Modem I can brows any website even can use apt-get without any problem.But cant use Ubuntu Software Center.Also cant connect to MateVPN.

But when I connect to a wi-fi network( I have just made a wi-fi hotspot in my mobile ) I can do anything.I can install software from Ubuntu Software Center and can connect MateVPN too.

It seems When I connect 3G Modem for some reason Network Manager cant understand that **"I have an active wireless network connection"!!!**

How can I solve that?

---


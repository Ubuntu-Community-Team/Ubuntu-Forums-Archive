---
title: "Develop Windows Apps on Ubuntu"
date: 2008-06-05
forum: General Help
---

### Post by mmDush on 2008-06-05
hi guys,
I was using ubuntu for a while now, Until now, I got this problem with this new project that I'm gonna get in few days, I have to develop a windows application for a company, since my lap-top and home pc are ubuntu, I can't format and install windows to them (can't be bothered, + I don't like it), so there anyway that I archive this without going through the hard format install way. :)

Thanx

---

### Post by estamand on 2008-06-05
How about install VMware server (free) and setting up a Virtual machine with XP/2000/Vista?

---

### Post by mtantawy on 2008-06-05
sorry i dont know a silution to ur request but i would like to ask you have you found an alternative to your programming software on ubuntu or linux in general??
ofcourse it will be developping linux apps....

i used to use visual studio .net 2003/5/8...

so if u've found any alternatives please tell me...

Thanx in advance
Mahmoud Tantawy

---

### Post by mrMango on 2008-06-05
Unfortunately, sometimes we're forced to do things for work that we don't particularly like, or want to do. Really the best way to develop windows apps is to do it on windows.

At any rate, because you don't want to format, I recommend you install VirtualBox (free) and set up a virtual machine with XP.

---

### Post by mrMango on 2008-06-05
> **mtantawy said:**
> sorry i dont know a silution to ur request but i would like to ask you have you found an alternative to your programming software on ubuntu or linux in general??
ofcourse it will be developping linux apps....

i used to use visual studio .net 2003/5/8...

so if u've found any alternatives please tell me...

Thanx in advance
Mahmoud Tantawy
If you have a seperate question, you should start a new thread.

Look into code::blocks, Eclipse, or (my fav) Anjuta.

---

### Post by ohiomoto on 2008-06-05
You can use VMware or remote into a Windows based machine.  I keep one of my Laptops running on XP for those times I need to do something in Windows.  It stays parked in my office and I remote into it from Ubuntu as needed.

---

### Post by sdennie on 2008-06-05
Another option would be to develop the app using gtk on linux.  There are gtk libs for Windows as well.  I developed an app in C++ using gtk and ported it to Windows for a friend and it was extremely trivial.

---

### Post by KingTermite on 2008-06-05
> **vor said:**
> Another option would be to develop the app using gtk on linux.  There are gtk libs for Windows as well.  I developed an app in C++ using gtk and ported it to Windows for a friend and it was extremely trivial.

That's what I was going to suggest too (that or Qt anyway). That way you can do all y our rigorous testing in Linux still.

Then you still should at least use VMWare or VirtualBox to test in Windows though.

---

### Post by MasterNetra on 2008-06-05
Yea you'd be better off using something like VMWare or Virtualbox. And installing WinXP into it. When your done with the project you can always just remove it with little issue. Downside is you will be using more ram for it. (Some for your Ubuntu and whatever is needed for running windows)

---


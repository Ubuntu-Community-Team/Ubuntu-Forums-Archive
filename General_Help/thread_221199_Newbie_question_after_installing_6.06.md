---
title: "Newbie question after installing 6.06"
date: 2006-07-22
forum: General Help
---

### Post by pvanosta on 2006-07-22
I just installed 6.06 on my laptop.
The config went fine and even the wireless network setup was OK.

Now, when I reboot, I end up at a command prompt.
How do I get to a desktop (KDE or whwtever)?

Thanks.

---

### Post by scxtt on 2006-07-22
have you ever gotten a graphical login? -- did you use the Desktop CD or the Alternate CD?

after logging in, type **startx** to see if you'll need to edit /etc/X11/xorg.conf ... there's also an Xorg reconfig command, but i don't remember what it is, i just edit xorg.conf :p ...

---

### Post by aysiu on 2006-07-22
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by pvanosta on 2006-07-22
I have never gotten a graphical login.

I downloaded the server CD, whatever that was called.

I will look at that other link in the responses.

---

### Post by scxtt on 2006-07-23
the server disk is intended to not use a GUI ... any particular reason you used it?

note, you can install a DE - generally as easily as **sudo apt-get install ubuntu-desktop** ...

---

### Post by T700 on 2006-07-23
This is getting crazy.  I know that there was a bug report/suggestion put in to more clearly label the downloads, but Canonical *really* needs to take action on this.  I can't imagine how many people download the server edition, boot up to a command line, and walk away from Linux forever.

Paul

---

### Post by jISh on 2006-07-23
> **T700 said:**
> This is getting crazy.  I know that there was a bug report/suggestion put in to more clearly label the downloads, but Canonical *really* needs to take action on this.  I can't imagine how many people download the server edition, boot up to a command line, and walk away from Linux forever.

Paul

And what kind of action do you propose? It says Desktop CD as the first section of the list. People should read things more carefully, and if they can't, they shouldn't be installing Linux.

---

### Post by scxtt on 2006-07-23
> **jISh said:**
> And what kind of action do you propose? It says Desktop CD as the first section of the list. People should read things more carefully, and if they can't, they shouldn't be installing Linux.i certainly agree w/ you on principal, but i do think it would be easy to put a disclaimer of "installing from the server disk will not provide you with a Graphical User Interface" ...

---

### Post by aysiu on 2006-07-23
In all fairness, the description of the Server install CD is this: > The server install CD allows you to install Ubuntu permanently on a computer.

---

### Post by T700 on 2006-07-23
> **jISh said:**
> And what kind of action do you propose? It says Desktop CD as the first section of the list. People should read things more carefully, and if they can't, they shouldn't be installing Linux.

That's exactly the attitude that helps keep Linux away from the majority of people.  This is widespread problem and the current solution is not working, so let's just tell people that they "shouldn't be installing Linux."

Paul

---

### Post by pvanosta on 2006-07-23
With all due respect, it says this about the DESKTOP CD:
"The desktop CD allows you to try Ubuntu without changing your computer at all,"

Then it says this about the SERVER CD:
"The server install CD allows you to install Ubuntu permanently on a computer."

Finally, there's the ALTERNATE CD:
The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

creating pre-configured OEM systems; 
setting up automated deployments; 
upgrading from older installations without network access; 
LVM and/or RAID partitioning; 
installing GRUB to a location other than the Master Boot Record; 
installs on systems with less than about 192MB of RAM. 

Based on the above, I assumed the Desktop CD was for running Ubuntu from the CD (which I have done in the past, withy a previous version).

So now I want a permanent install and I read that 6.06 supports my WiFi card out of the box, which was my only objection to switching to Linux on my laptop, so which CD do I pick, based on the descriptions?
Right.
The SERVER CD

I have just finished downloading the alternate CD and will reinstall tomorrow.

But one of the above posters is right. Stuff like this is enough to make many people reach back for their easy, painless Windows install CD.

I'll let you know how I get on tomorrow. Thanks for your help.

---

### Post by scxtt on 2006-07-23
i agree that it's not entirely clear, and i don't think anyone is trying to blame you or cast anything negative vibes in your direction ... and you can get a gui (relatively painlessly) if you've installed server, tho for 1st-timers i don't know how you could possibly know that ...

linux is, and always will be, is OS of choice - and that can be hard to deal with ...  windows is 'painless' in that it doesn't offer you choice ... it's just give and take ...

---


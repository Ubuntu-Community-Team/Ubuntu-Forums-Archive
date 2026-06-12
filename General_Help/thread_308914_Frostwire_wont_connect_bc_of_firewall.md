---
title: "Frostwire wont connect b/c of firewall"
date: 2006-11-28
forum: General Help
---

### Post by JoeC21 on 2006-11-28
I am trying to use frostwire but it never connects to the network because it says it has detected a firewall.  How do I tell what firewall is running?  As far as I can tell I dont have firestarter or guarddog installed and those are the only firewalls that I know of for linux.

Any ideas on what to do to get frostwire to connect?

Thanks,
Joe

---

### Post by taurus on 2006-11-28
You can install firestarter and use it to configure your firewall!  Does your computer connect to a router or something?


```
sudo aptitude update
sudo aptitude install firestarter
```
System -> Administration -> Firestarer

---

### Post by klahjn on 2006-11-28
used the new gnutella.net and now it works perfectly...thanks for posting that.  It was quite annoying.  Thanks for all the hard work

---

### Post by JoeC21 on 2006-11-30
@Taurus - I installed Firestarter but I am unsure how to tell it to allow Frostwire.  If I disable the firewall altogether though Frostwire still says it detects a firewall.

I am connecting through a router.  It's a Dlink DIR-625.  Do you think it might be a built in firewall?

@klahjn - I am not exactly sure what you are talking about?  I checked gnutella.net.  Are you using a different program to access the network? What one?

Thanks for the help and sorry it took so long to respond.

Joe

---

### Post by RAOF on 2006-11-30
Since you're behind a router, the internet has no way of contacting you (they'll only contact the router, which has no idea where it should go).  You'll need to set up *port forwarding* on your router for whatever ports frostwire needs (it'll say somewhere in its documentation).

You want to make your router forward any connection on that port to the computer you're running on.

---

### Post by JoeC21 on 2006-12-02
I followed the guide here [http://portforward.com/english/routers/port_forwarding/Dlink/DIR-625v1.04/Limewire.htm](http://portforward.com/english/routers/port_forwarding/Dlink/DIR-625v1.04/Limewire.htm) and it still wont work. The only thing I can see that is different is for the name.  They used Limew1, I just used Frostwire for the application name.  Does frostwire have a different name I should enter there?

---

### Post by taurus on 2006-12-02
Make sure the port that you use with frostwire is the same port that you open in your router!!!

---

### Post by JoeC21 on 2006-12-03
> **taurus said:**
> Make sure the port that you use with frostwire is the same port that you open in your router!!!

Yeah, both places it is the same port.  I went back and tried with serveral differt ports and each had the same result.  I tried putting the computer into what the router called the demilitarized zone.  It said to use that as a last resort but Frostwire still wouldnt connect because of a firewall.

---

### Post by tarreaga on 2008-02-23
I have a 2Wire Router.  Found a fix online.  Did not have to forward a port or change any Frostwire settings.  Go to this site [http://www.mybloop.com/FTA/fixconnecting.zip](http://www.mybloop.com/FTA/fixconnecting.zip).  Download and install than restart Frostwire.  Worked for me.

---

### Post by cbiere on 2008-02-25
Your URL points to a ZIP-packed executable for Windows XP. How this going to help anyone with a Linux-based operating system like Ubuntu? Even if it would work who in his right mind would download and execute some dubious program from an unknown website? Who says this doesn't contain a virus or applies some dangerous modification to FrostWire? I find it quite interesting that you bothered to sign up just to link to this file but didn't even take the time to think about in what kind of forum you are posting.

---

### Post by tarreaga on 2008-02-25
I was only trying to help since it worked for me.  And anyone with a brain would no to run a virus check on the program before they in stall it or any other program.  Apparently you dont have a brain or you are just basically rude!

---

### Post by tarreaga on 2008-02-25
Forgive my previous rant as this is a forum for help not criticism.  Here is a link to a page where there is possibly a fix for Linus.

[http://www.gnutellaforums.com/frostwire/63426-worked-fix-starting-connection-problem-linux.html](http://www.gnutellaforums.com/frostwire/63426-worked-fix-starting-connection-problem-linux.html)

---

### Post by dunnac on 2008-02-28
This worked for me from the Frostwire Community:

[http://www.frostwire.com/forum/viewtopic.php?t=2884](http://www.frostwire.com/forum/viewtopic.php?t=2884).

---

### Post by micro. on 2008-06-01
[FONT="Comic Sans MS"][SIZE="2"]http://www.frostwire.com/forum/viewtopic.php?t=3398&highlight=guarddog

I must give this individual credit since I feel the same way sometimes.

This link is for a fix to Frostwire's connection issue while running 'guarddog.'  It is but one way when using this firewall.  You could always just allow the specific port frostwire tries to use.[/SIZE][/FONT]

---


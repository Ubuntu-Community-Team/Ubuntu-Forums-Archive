---
title: "can't find server."
date: 2023-07-02
forum: General Help
---

### Post by jaxom98 on 2023-07-02
Dual boot:  win10 /Ubuntu 20.04.3 OS

Problem: In website   wwwtractorbynet.com I get frequent error messages stating website can't be found. This only hits the Ubuntu os and does not affect windows.  
There are 2 variations: 1)won't open website at all.  error mesage: 

We can’t connect to the server at [www.tractorbynet.com]("http://www.tractorbynet.com").

If that address is correct, here are three other things you can try:

    Try again later.
    Check your network connection.
    If you are connected but behind a firewall, check that Firefox has permission to access the Web.

2) on a multi page thread the same error message comes up going from 1 page to the next, ie click on "next" . Clicking on the next sequential page number is slightly more reliable.  A  work around is to jump a couple of pages ahead or back then go to the desired page, note , this does not always work.
    Sometimes the problem is so bad  the site is unuseable.
     This has been going on for about 2-3 months.    
Has anyone run into this before?

---

### Post by guiverc on 2023-07-02
I'll just comment.

You mention your system is dual boot, thus only windows or Ubuntu can run at the same time, so if your site is being handled by Ubuntu and you're using windows at the time, the website being down is expected.  (*unless I misunderstood your details*).

Secondly your details show you've not applied security fixes to your Ubuntu system in some time, eg. [https://fridge.ubuntu.com/2022/02/25/ubuntu-20-04-4-lts-released/](https://fridge.ubuntu.com/2022/02/25/ubuntu-20-04-4-lts-released/) shows that the 20.04.4 ISO was released back in February 2022, but installed systems upgraded **before** that date too, so you've not applied security fixes for some time, thus I'd check out the health of your system.  A fully upgraded system has reported itself as [20.04.6]("https://fridge.ubuntu.com/2023/03/23/ubuntu-20-04-6-lts-released/") for some time now too.

---

### Post by jaxom98 on 2023-07-03
Hello guiverc, The problem only hits ubuntu os NOT windows.

Using terminal to update does not work as terminal will not allow the password to be entered. The curser blinks like it is waiting for input but will not accept input.  What is an alternative method to update?   Please keep things simple.

---

### Post by deadflowr on 2023-07-03
> Using terminal to update does not work as terminal will not allow the password to be entered. The curser blinks like it is waiting for input but will not accept input.
?
The password field is purposefully blank with feedback disabled..
Type the password and hit enter.

---

### Post by jaxom98 on 2023-07-03
Ubuntu20.04 is now upgraded to 20.04.6, it was slow going as there was a broken index blocking things.
The can't find server error message  has changed to "Page could not be loaded."  However I was able to brouse 20-25 pages before this happened, so a nett gain.

In terminal when updating I kept getting an error message saying to run "dpkg"  and "--configure -a"  manually what does this refer to?

---

### Post by SeijiSensei on 2023-07-04
It means some packages are not entirely installed. Run that command with sudo.
```
sudo dpkg --configure -a
```

---

### Post by jaxom98 on 2023-07-05
Hello SejiSensei, I ran the dpkg command , however I am unsure what if anything happened. It wanted my password per normal, but after that it was a black hole. There was no dialogue box saying finished or wanting a restart or anything.

The update also fixed the sluggish boot time.

---

### Post by SeijiSensei on 2023-07-05
Usually it prints out a list of each package being upgraded. DK why you didn't see that.

---

### Post by jaxom98 on 2023-07-06
When I did the initial upgrade I got a window that showed a list of packages.  Then after sorting out the boken index(not sure how) I got a window offering a partial upgrade as "some dependancies are **********"(didn't make a note)  
I clicked on the partial upgrade.  
Subsequently I noted the improvment in accessing tractorby net website, and the return of the usual boot up time.
 You gave me the dpkg command.
I tried to run it but there was no dilogue box appear, so I don' know if it worked or failed.
I reran the dpkg command .
terminal : 
duncan@admin-P55-gigabyte:~$ sudo dpkg --configure -a
[sudo] password for duncan: 
duncan@admin-P55-gigabyte:~$ (blinking curser)

there was no dialoge box or anything further

---

### Post by jaxom98 on 2023-07-07
The gremlin is back, I am unable to reliably enter website tractor by net directly via bookmarks or via manual entry.I get error message 
"Unable to find site" (verbatim, as gremlin is hiding now that I want to copy the error message)

Also when I do get into site and am reading multi page threads I get this error messsage:
The requested page could not be loaded.  
[LIST]
[*]Check your internet connection and try again.
[*]Certain browser extensions, such as ad blockers, may block pages unexpectedly. Disable these and try again.
[*]TractorByNet may be temporarily unavailable. Please check back later.
[/LIST]

---

### Post by TheFu on 2023-07-07
Seems like misconfigured DNS settings to me.

---

### Post by jaxom98 on 2023-07-10
Hello guiverc, dead flowr, Seiji Sensei, and The Fu, thank you for your time . Please consider this thread closed. I don't have the knowledge to sort this. This thread should have been put in absolute beginner, not general help.
Thank you again for your time.

---

### Post by TheFu on 2023-07-10
Fixing DNS issues isn't hard and they are common enough in recent Ubuntus (since 20.04) that you can find at least 20 threads in these forums for possible fixes.
I'm not the person to help, since I rip out all the default DNS stuff in Ubuntu, but I think there's a /etc/systemd/resolved.conf file (or named something like that) which just needs 2 lines modified to point at primary and secondary DNS server IPs.  systemd-resolved is an abomination, IMHO.  The only thing worse was resolveconf.

1.1.1.1 and 1.0.0.1 would be the DNS IPs that I use and should work worldwide (except China). The lines should look like this:
```
DNS=1.0.0.1
FallbackDNS=1.1.1.1

```

I'm making 50 assumptions. If any 1 of those isn't true, then I'm wrong. You don't seem interested in running the 5 commands to figure out the real issue for certain.

---


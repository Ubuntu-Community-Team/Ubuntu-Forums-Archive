---
title: "home network"
date: 2015-04-13
forum: General Help
---

### Post by Pedroski55 on 2015-04-13
I seem to be having trouble accessing other computers attached to my router. 

Could someone please tell me what I need to read up about, which program I may need to install, or if the router settings must be changed to do this. Lets say at first connect 2 computers running Ubuntu 14 through my router. Later I'll try connecting to a win comp, or a mobile phone. Start out easy! I just want to learn how this is done.

Do I need to designate 1 comp as a 'server'? I believe I will only be able to access a designated 'public folder', but that's fine.

Once, I set up apache2, then I could enter the name of my computer in Firefox and call up my simple webpage, but it was not possible to do that from another computer at home which was also connected to my router. Other computers did not find my computer, 'pedro-bedro'.

Entering 192.168.0.X gets me into the router, not the computer at home with that ip.

I just need some tips about what to read up on for this specific task.

---

### Post by dino99 on 2015-04-13
you might found what you need here: [https://www.google.de/search?q=ubuntu+bluetooth+troubleshot&oq=ubuntu+bluetooth+troubleshot&aqs=chrome..69i57.23806j0j8&client=ubuntu&sourceid=chrome&es_sm=93&ie=UTF-8#q=ubuntu+sharing+router](https://www.google.de/search?q=ubuntu+bluetooth+troubleshot&oq=ubuntu+bluetooth+troubleshot&aqs=chrome..69i57.23806j0j8&client=ubuntu&sourceid=chrome&es_sm=93&ie=UTF-8#q=ubuntu+sharing+router)

---

### Post by 1clue on 2015-04-13
Let us know about your setup, and your intentions.

It's pretty obvious from your post that you don't understand  networking.  That's not a bad thing, but if you intend to do any amount  of some sort of computer work, even managing your own home, then it's a  really good idea to learn the basics at least.  
[LIST=1]
[*][https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)
[*][https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[/LIST]

If you have a typical wireless or wired router and have computers just plugged into it and automatically configured, then you don't need to have anything extra for a test inside of your network.  If you intend a box to be a server (like http) then you might want to configure a static IP address for that one.

So first:
[LIST=1]
[*]What variant of Ubuntu are you using?  Ubuntu, Xubuntu, Kubuntu, server, ...?
[*]What other operating systems are involved in your issue?  (Windows, Mac, *buntu, ...)
[*]Do all your boxes have Internet access?  Meaning, can you go to [http://www.ubuntu.com/](http://www.ubuntu.com/) and get the page?
[LIST=1]
[*]If not, then you need to make that happen.
[/LIST]

[*]You should be able to ping your router from each box.  Based on what you posted I'm guessing that will be 192.168.0.1.
[*]You should be able to ping each computer from the other computer(s) on your network.
[*]Do you intend to learn some aspect of computing for your work, or do you just want to experiment?
[/LIST]

---

### Post by pmi2 on 2015-04-13
I installed Samba, from the official Ubuntu repositories, for basic sharing of folders with a couple other computers running Windows, and another version of Linux.  Samba has been around for over 20 years, and it is reliable while hiding a lot of the network details from a casual user.  Here is a short tutorial on how to set it up in Ubuntu 14.04:

[http://ubuntuhandbook.org/index.php/2014/05/ubuntu1404-file-sharing-samba/](http://ubuntuhandbook.org/index.php/2014/05/ubuntu1404-file-sharing-samba/)

---

### Post by Habitual on 2015-04-13
[http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)

---

### Post by Pedroski55 on 2015-04-13
Thanks for the replies. I will read all the links, see if I can make it work.

My setup is normal, I am a customer of China Telecom, which is my isp. They gave me a router with 4 LAN sockets. All three laptops can access the internet. I would like to know how to connect to other computers connected to this router.
Personally I always use Ubu, this is 14.04.something. To start with, I just want to connect my old laptop and my new laptop, just to see how that is done. Then try to connect to a Win comp and maybe a phone.

---

### Post by 1clue on 2015-04-13
So you have multiple linux boxes on this network?

Sorry I'm on my phone right now so can't give examples but you should be able to ping the ip address of another box.

Then if you have ssh server on one you can login with "ssh you@192.168.0.x" where x=the remote machine's last ip quadrant.

---


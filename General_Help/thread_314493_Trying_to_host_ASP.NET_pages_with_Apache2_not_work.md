---
title: "Trying to host ASP.NET pages with Apache2 not working"
date: 2006-12-07
forum: General Help
---

### Post by deejross on 2006-12-07
First of all...  ](*,) 

I am REALLY trying to maintain a calm tone right now, so I apologize in advance if this post seems "pissy". It just seems like everytime I do something advertised as "simple" and "easy", it blows up in my face.

On to this week's topic...Running ASP.NET 2.0 applications on Apache2. I followed the [mod_mono]("https://help.ubuntu.com/community/ModMono") tutorial on how to get it to work, but as usual, it didn't work and everytime I google a description of the problem, I get tutorials on the same topic, to accomplish the same thing, none of them work, and no two are alike. So I would REALLY like someone to let me in on the RIGHT way to do this.

I am running Edgy (upgraded from Dapper) on a Desktop machine that already runs PHP on Apache2. Following the mod_mono tutorial of installing, I installed libapache2-mod-mono and mono-apache-server2. Then ran "sudo a2enmod mod_mono" which said something like "mod does not exist". After playing around and confirming with Synaptic it was installed, I uninstalled and reinstalled. This time it told me the mod was already enabled. Great. I went into the "/etc/apache2/mods-available/mod_mono.conf" file and changed the switched the comment lines as instructed.

Then it got down to "4) Configure your web applications". And this is where I got confused.... What the hell are .webapp files? So I skipped that part seeing as how that tutorial is very incomplete if it doesn't explain what they are, why you need them, and what you need to do to get them to work. I restarted Apache2 and I put a simple "Hello World" asp.net app in the www directory, but when I ran it, Firefox wanted to download it.

This is the part where I Google until I drop...Reading and changing config files until I get cross-eyed. I eventually got it to try and show the page, but then it gives me "503 Service Temporarily Unavailable". And Googling this returned one guy with the problem, and he said he uninstalled all the mono stuff and reinstalled....so I did...in Synaptic, I did a complete removal. Then I reinstalled, and I'm still getting the 503 error.

Again, I'm sorry if I'm ripping anyone's head off, but I am very frustrated with Ubuntu right now and I would really appreciate your help with this one. So thank you in advance for any help you can give me.

Ross

---

### Post by deejross on 2006-12-10
No one has an answer? :(

---

### Post by chazbo877 on 2006-12-13
A useful source is [http://ubuntuforums.org/showthread.php?t=225454]("http://ubuntuforums.org/showthread.php?t=225454").  In edgy, mono wouldn't even install from synaptic, but this worked.

Also, if your browser allowed you to download your asp file, that means the extension you wanted to use is not configured correctly for mono.  In the default configuration /etc/apache2/mod_mono.conf does not setup .asp files, it only sets aspx.  

I think that .webapp files are an asp thing, not mono, but this could be very wrong.  regardless, i didn't need to create one to get my stuff working

I'm new to mono as well, but I hope this helps

---

### Post by deejross on 2006-12-13
Thanks for your reply. I did not try to compile mono from source, so maybe that's what I need to do the trick. I will give it a try tomorrow and let you know how it goes.

Thanks again

---


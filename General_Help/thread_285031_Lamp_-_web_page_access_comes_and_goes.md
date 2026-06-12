---
title: "Lamp - web page access comes and goes"
date: 2006-10-26
forum: General Help
---

### Post by mkclinux on 2006-10-26
Installed ubuntu lamp server, all ok.  When I browse from a workstation to a test page i get there but after a minute or two I get Page Not Found.  Only way to correct is ifdown eth0 then ifup eth0 or 

/etc/init.d/networking restart

or

wait awhile and sometimes it is up and sometimes down.

Then I can navigate the web page for about 2 or 3 minutes and then page not found.

The whole time I have a constant ping going with zero packet loss during down time so the network is still up.

Also, with putty, I get a network error message but after doing the above I immediately get in.

Thanks

---

### Post by hartunnoo on 2006-10-26
try to reboot your system. sudo shutdown -r now

---

### Post by funkyade on 2006-10-26
Sounds like a faulty NIC... However, further info needed>>>

Are you doing ```
/etc/init.d/networking restart
``` on the server or the workstation?

Is this a wireless network or a wired one?

Are you using a router or just a switch/hub?

What version of Ubuntu are you using?

Can you initiate and complete a file transfer during this time?

Some semi-random questions for you!

---

### Post by mkclinux on 2006-10-26
posted below.

---

### Post by mkclinux on 2006-10-26
Sounds like a faulty NIC... However, further info needed>>>

/etc/init.d/networking restart is on the server

Is this a wireless network or a wired one?  wired

Are you using a router or just a switch/hub? switch/hub

What version of Ubuntu are you using? 6.06

Can you initiate and complete a file transfer during this time?

Ok, for this question, time for honesty, I am so new at this that I haven't been successful at setting up ftp or samba.  I have all windoz ... aspiring to escape bill, so every time I try to login from my winxppro, I get stopped with enter user id and password ... so I enter steve and then the password and it comes back with winmachinename\steve and keeps asking for a password.  Kinda shtuck.

Some semi-random questions for you!

Thanks for responding.

A little more info: putty running on my winxppro dies the sametime the browser dies on the winxppro but the browser to the test page on the ubuntu server still works.

...Something more interesting, I am pinging from winxppro to ubuntu server by way of host name ... zero packet loss.

But, while pinging from ubuntu server to winxppro by way of ip address, (it doesn't see the win host name), right when putty dies and throws error and browser can't get to the web page, the ubuntu ping to winxp **_pauses_**.  Waiting a minute shows the ping start up again and then putty and browser work.

All the while, that I am pinging ubuntu to winxppro I am ping [www.yahoo.com](www.yahoo.com) and there is zero packet loss ... it keeps going even when the ubuntu to winxppro ping pauses.

The pause in the browser happens about every 3 to 5 minutes and lately only lasts a minute or 2.

Thanks.

---

### Post by matthewstory on 2006-10-27
yeah man, sounds like a faulty NIC to me too

---

### Post by mkclinux on 2006-10-27
](*,) UhOh, I had a ping going on winxppro ping the linux box and when I turned off linux to replace the nic the winxppro ping just kept on a goin' hmmmmm....

I forgot awhile back when I got Vonage that I set the Linksys voip box to the static that I chose for the linux box.

Problem resolved.

Thank you for your responses.

Steve

---


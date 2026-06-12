---
title: "myth tv info please, im new.."
date: 2008-05-27
forum: General Help
---

### Post by no1cares on 2008-05-27
first:
 I am interested in the myth tv. was wandering if anyone uses it... if they could give some input on it... likes, dislikes, usefulness.. and maybe a simple explanation on how it works?? does it get the tv from the internet or do u need to hook up a cable cord to your computer??? im currently reading the website to help explain, but i figure input would help the best.

second:
The website documentation page lists some prerequisites. (link is to website) [http://www.mythtv.org/docs/mythtv-HOWTO-3.html#ss3.1](http://www.mythtv.org/docs/mythtv-HOWTO-3.html#ss3.1)
how do i check and make sure i pass all these.. were are computer specs listed, how much memory i have.. etc.. i have a 500gb external hardrive can i store the tv on that??
more importantly... the firewall/tcp ports... where do i check that.
> You must ensure that any firewalls (either hardware, or a software firewall installed by your distribution) will not block access to the ports that will be used by the MythTV clients and servers on the "inside" LAN. The ports for MySQL (TCP port 3306) and mythbackend (TCP ports 6543 and 6544) must be open. It is strongly recommended that you do not expose the MythTV and MySQL ports to the Internet or your "Outside" LAN.


fourth:
 how and what do i need to download... theres 61 packages in the Synaptic Package Manager. or do i download from the website. 

any help would be great.
thanks.

---

### Post by Monicker on 2008-05-27
I've been using mythtv for a couple of years now, though not on Ubunutu specifically.  I use it to record television shows and watch them at the time of my choosing.  You will need a capture card in order to record the television signals with mythtv.  You can also use mythtv to listen to mp3s and other media, though I do not use it for that myself.

Mythtv uses a mysql database to store all of its configuration settings, along with the information about the recordings.  The 3 main pieces are the mysql database, the machine with the capture card (backend), and the frontend for viewing.  All of these can be one computer, or on different computers.  I usually just watch the shows on my computer after recording them, though for my wife and kids I will often burn the shows to a rewriteable dvd so that they can watch them on the regular television set using our dvd player.  Occasionally I will watch shows that are stored on my desktop from my laptop.  When the pieces are separate is when you have to worry about firewalls so that communications between them is not interfered with.


You might want to look at mythbuntu, which has all of the mythtv packages already in it.

[http://www.mythbuntu.org/]("http://www.mythbuntu.org/")

If you do decide to get a capture card for recording television, be sure to get one which does hardware encoding directly on the card. Software encoding can put quite a load on your cpu.

Also take a look at the mythtv wiki.  It contains lots of good information.

---


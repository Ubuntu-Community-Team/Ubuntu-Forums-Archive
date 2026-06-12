---
title: "Azureus troubles"
date: 2007-07-27
forum: General Help
---

### Post by alalusim on 2007-07-27
ive been using azureus for a while and though i periodically get average/good download speeds many times its like this screenshot:

[http://img256.imageshack.us/img256/7244/screenshotvo8.png](http://img256.imageshack.us/img256/7244/screenshotvo8.png)

im pretty sure ive done all the necessary port forwarding stuff (the NAT test and smileys are green) but it always ends up not downloading

can somebody please give me some advice?

---

### Post by alalusim on 2007-07-28
is this post in the right section?

---

### Post by cold_light on 2007-07-28
Hi, this is a little off topic, but I was wondering what that skin you were using was.

It's really nice.

---

### Post by Gausian on 2007-07-28
looks to me like you're just not connecting to enough peers/seeders.  this could be because of you settings, so you could try increasing the total # of connections.

also you have way too many torrents going at once.  your total #  global connections are spread over the torrents.  BT isnt emule or kazaa, sharing lots of torrents doesnt make you a good sharer. but being able to finish a download quickly and seed it does.  thus, fewer torrents is better.

---

### Post by alalusim on 2007-07-28
too many torrents going at once is part of the problem, if i queue new torrents they end up downloading because there are no/few connectiosn and the only solution i can think of is to stop most of them until the first few finish.  

i think the theme im using is called vista ice and i probably got it off of GNOME-look.org.  you'll need beryl/emerald to use it

---

### Post by kelvin spratt on 2007-07-28
Try changing your listening port try between 6,000- 6,300 limit your up load speed and turn Beryl off as its draining your resources, turn off safe peer if your using it as it won't stop people from knowing your Ip. or what you are downloading, stop all other downloads and select torrents with lots of seeds and less leechers
then you will hopefully get better download speeds i max out my connection a lot, also your ISP may be capping you to about 25kbs if so you have a problem.you can try encryption but it does not allways  work,

---

### Post by Ansible on 2007-07-29
I've had the same problem with just one torrent and then two torrents.  I 'fixed' it by restarting azureus.  The wierd thing with the two torrents was that they said 95.7 and 97% completion, but then under ETA they said Finished.  After I restarted they showed up in the seed section.  

I think its a bug with azureus.  Maybe an older version would work better?  I'm using 2.5.0.0.

---

### Post by Ansible on 2007-07-29
So I filed a bug at sourceforge re this issue, and got this reply:

"this is obviously not an official Azureus build but a distro version.
Download an official tarball(!) from azureus.sf.net and make sure you hava
sun java installed and not gnu java."

Ok, so I went to the synaptic package manager and selected sun-java6-jre.  Downloaded the azureus tarball and unpacked it into my home dir, running it from there.  It tried to do an update but failed because of permissions.  So now I've got 2.5.0.4.  

When I go to the about menu Azureus, under the system section is says this:

Java 1.4.2
 Free Software Foundation, Inc.
SWT v3320, gtk
Linux v2.6.20-16-generic, i386

That would seem to imply that I'm still running gnu java and not sun java.  No clue on how to switch between these.

---

### Post by Ansible on 2007-07-29
Ok, so found out how to do that.  This is what I did:

bb@Gigantor:~$ update-java-alternatives -l
java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1041 /usr/lib/jvm/java-gcj
bb@Gigantor:~$ sudo update-java-alternatives -s java-6-sun
Password:

I hope it worked because I got a lot of messages like this:

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar

<etc etc, about 50 more of those>

Anyway now Azureus comes up with this in the system section:

Java 1.6.0
 Sun Microsystems Inc.
SWT v3236, gtk
Linux v2.6.20-16-generic, i386

If this has solved the problem I'll post back in a few days.

---

### Post by Ansible on 2007-07-31
So, I said I'd post back if there were any problems.  I did run azureus 2.5.0.4 and it was fine.  But I only seeded, and didn't download, so who knows.  With sun java installed, the old 2.5.0.0 version just quits immediately - this is the version that comes up if you select Azureus in the firefox 'open with' dialog.

I do consider this 2.5.0.0 problem a bug with ubuntu - AZ should be distributed with dependencies on sun java if it won't run properly with the free java.  To do otherwise is just wishful thinking and makes life more difficult for people that actually want to use the software.  Pretending that a FOSS solution is ready for prime time when it clearly is not is counterproductive.  I guess its possible this just didn't come up in testing, but if this is a known issue I'll be really annoyed.  

I've switched over to Deluge instead, its very fast and lightweight.  So I probably won't spend more time investigating Azureus any further.

---

### Post by alalusim on 2007-07-31
ive done most of the things that youve said and everything seems to be fine now in terms of both seeding and downloading

sorry that it didnt work out for you but thanks

---


---
title: "Linux equivalent of Microsoft stuff"
date: 2007-11-18
forum: General Help
---

### Post by zemeron on 2007-11-18
Hello, everyone I'm kinda new to Linux and I'm trying to determine a couple of things from people who have had some professional experience. For reference I am a systems consultant that works on Windows systems almost exclusively (the only time I see Linux is on network appliances). As such I am trying to learn how Linux handles things in comparison to the Microsoftian way.

1. Is there a linux solution that rivals outlook/exchange? I've tried evolution with exchange but its exchange backend keeps failing and in any event that would still require Microsoft on the backend. Thunderbird is great for email but those who use Outlook know that it is more than an email client. It is more like a task command central.

2. Does linux have anything similar to GPOs in Windows for administration purposes?

3. Does linux have anything similar to roaming profiles and remote folders like Windows? (kinda falls in the same category as the above question but it is different enough that I thought I would seperate it out)

4. Does linux have anything like active directory? I've seen LDAP but it is very limited compared to AD in that AD integrates with all of Microsoft's services: exchange, dns, printers, etc...

Any other windows vs linux methodolgy would be helpful.

Also I have a couple of picky little things that are annoying me that if anyone knows the answer to I would be appreciative.

5. Is there a good GUI program for configuring mouse buttons? It seems odd to me that to configure something as simple as a 5 button mouse you have to resort to modifying xorg.conf. Picky I know but still I swap out mice fairly often between home and work as I have a 5 button wireless mouse at home and carry around a 3 button mouse for work.

6. Video playback. I'm using VLC since thats what I used under Windows. I like using the x11 video output modules because it works with the graphical effects of Compiz (which is awesome) but the fullscreen display looks bad. XV playback has a nice fullscreen but doesnt work with Compiz effects naturally as it doesnt pass through the x11 system. Is there a way to specify XV for fullscreen and X11 for regular playback?

---

### Post by Flying caveman on 2007-11-19
[http://www.linuxalt.com/](http://www.linuxalt.com/)

---

### Post by ubuntu27 on 2007-11-19
Check out the following sites:

[Linux Alternative Project]("http://www.linuxalt.com/")

[Open Source Alternative ]("http://www.osalt.com/")

---

### Post by benjamin222 on 2007-11-19
[http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)

thats a good one too.. mostly the same list though

---

### Post by zemeron on 2007-11-19
Thanks for the replies but unfortunately there is nothing on those lists that relate to the services I asked about other than the Linux programs that I listed which arent up to snuff. 

Would it be correct to assume that Linux lacks methods or anything comparible to those windows services/programs?

PS. I dont really care if it is commericial or free software. I'm mostly trying to evaluate where Linux stands as far as being a competitive replacement for Microsoft in a workplace.

---

### Post by daengbo on 2007-11-19
1. Is there a linux solution that rivals outlook/exchange? 
Quite a few, but you'll need to shell out money for them. If you're looking for something to natively connect with Eschange (as opposed to using the web interface), you're probably out of luck. MS ties those two products together really tightly. If you're at work and using Exchange, stick with MS Windows. If you're handling your own network, find something more robust than Exchange and standardize on that.

2. Does linux have anything similar to GPOs in Windows for administration purposes?
The standard Unix method supports groups and LDAP does, as well. Any graphical user management tool will include group stuff. How you set that up is up to you.

3. Does linux have anything similar to roaming profiles and remote folders like Windows?
Mount /home through NFS. It pre-dates roaming profiles by years. It doesn't need to cache anything locally or save on logout, either. It's all network-transarent.

4. Does linux have anything like active directory? I've seen LDAP but it is very limited compared to AD in that AD integrates with all of Microsoft's services: exchange, dns, printers, etc...
LDAP will handle all that stuff. There are packages in the repositories for printers, DNS, etc. Getting LDAP set up is kind of a pain, though. Once it's set up, there's no pulling it down, though. Look at the eBox project for the only simple LDAP setup I've ever seen.

Any other windows vs linux methodolgy would be helpful.
The general one is to approach problems with a Unix mindset, not a Windows one. Use small tools which do one job extremely well and can be piped together. Script whenever possible, Don't think about how you would do the  task on Window -- that's only point you in the wrong direction.

5. Is there a good GUI program for configuring mouse buttons? 
No. User modification of the graphic system is something new in the Unix world. Xrandr (the extension which allows a user to change the graphic layer) is only at version 1.3. Heck, Gutsy is the first Ubuntu with a graphical method for configuring X. Editing plain text files is the Unix way, though. I expect tools like that to show up really soon. Most people have more important graphical issues to work on, like Bulletproof X.
6. Video playback. I'm using VLC since thats what I used under Windows. 
Why not use the Ubuntu default player? It works in both cases.

---


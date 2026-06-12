---
title: "Lab Help"
date: 2007-02-03
forum: General Help
---

### Post by CompTeach on 2007-02-03
Hello everyone,
I am a computer teacher for 6th, 7th, and 8th graders at a public middle school. We currently have 32 computers running Windows XP connected to the school wide network through a switch in the closet. The performance of these computers and the network seems to be getting worse every day (almost to the point where I can't teach), also I think it would benefit the students to show them a different operating system than Windows. I have already set up one of the computers to dual-boot Ubuntu with Windows (The Internet through the school network worked fine in Ubuntu). 

My question is:
Can I set up a Linux network using the schools equipment, still maintain Internet access, create a file server and a way to let students log into the different machines using a central user name? Can this be done without disrupting the campus network? (the IT people will need very little excuse to stop this and will provide me with no help). Also any advice you can give me on software, distros, etc. would be greatly appreciated, I am not a Linux newbie but I am pretty close to being one. The schools network is a standard windows domain running Server 2003. I have a server that I built using the E6300 Conroe, 2 GB of RAM and two NIC cards. Is this sufficient for a server? Can I connect it through the switch (Cisco)?

---

### Post by taurus on 2007-02-03
For school, you may want to check out Edubuntu.  I am sure the kids would love to play around with it.

[http://www.edubuntu.org/](http://www.edubuntu.org/)

---

### Post by ardvark71 on 2007-02-03
> **CompTeach said:**
> 
The performance of these computers and the network seems to be getting worse every day (almost to the point where I can't teach)

I would be curious as to the reason for this. Do your IT folks routinely check these systems for spyware, viruses and perform routine maintenance?

Best Regards....

---

### Post by CompTeach on 2007-02-03
> **ardvark71 said:**
> I would be curious as to the reason for this. Do your IT folks routinely check these systems for spyware, viruses and perform routine maintenance?

Best Regards....

I know they have Norton running over the network and they talked about buying some type of appliance to keep the spyware and spam down.  They do run the defragger from time to time (it should be on a schedule, but they won't do that for some reason).  The profiles are stored locally and every once and a while they will come in and erase them.  Some still have 2 years worth on them.  Their desktops and documents folders are redirected to a server.

The computers are P4s so they should be fast enough.  They do only have 256 megs of ram which I think is part of the problem.  The Internet seems to work fine, but Office runs very poorly, especially the first time the students use it on a computer.  The installer can take up to 10 minutes to finish (a very long time in the classroom).  Very often I watch the various windows load on the screen, instead of coming up all at once, they start at the top and very slowly work their way down.  They also lock up a lot and I will have to restart the computer, since task manager is disabled on the student accounts.

They have been adding a lot of computers (especially wireless notebooks) to the network so that may have something to do with it.  I know a little bit about networking but not enough to tell if the problem is with the network or the workstations.

---

### Post by ardvark71 on 2007-02-03
> **CompTeach said:**
> I know they have Norton running over the network and they talked about buying some type of appliance to keep the spyware and spam down.  They do run the defragger from time to time (it should be on a schedule, but they won't do that for some reason).  The profiles are stored locally and every once and a while they will come in and erase them.  Some still have 2 years worth on them.  Their desktops and documents folders are redirected to a server.

The computers are P4s so they should be fast enough.  They do only have 256 megs of ram which I think is part of the problem.  The Internet seems to work fine, but Office runs very poorly, especially the first time the students use it on a computer.  The installer can take up to 10 minutes to finish (a very long time in the classroom).  Very often I watch the various windows load on the screen, instead of coming up all at once, they start at the top and very slowly work their way down.  They also lock up a lot and I will have to restart the computer, since task manager is disabled on the student accounts.

They have been adding a lot of computers (especially wireless notebooks) to the network so that may have something to do with it.  I know a little bit about networking but not enough to tell if the problem is with the network or the workstations.

Hi...

The network, or the internet, by itself wouldn't affect the speed of the individual machines, it would just affect how quickly you could download content. Yes, you're right about the memory, 256 is the bare minimum, 512 and above is more ideal. Since your IT is just talking about something to eliminate spyware, it's a good guess as to what's on these machines. I would download and run Adaware and Spybot on each of these systems. I would assume Norton is playing a role here too, as you mentioned, but I don't see them changing that. ;) 

If you feel up to it, give Edubuntu a try and see what happens. You may find it more suitable. I'm not sure but it may even include a "live" feature, like Ubuntu and Kubuntu, so you can see what is compatible and what isn't.

Best Regards...

---


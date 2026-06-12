---
title: "fan running wild for years and a message that popped up and I clicked, seem to fix it"
date: 2021-08-03
forum: General Help
---

### Post by pierreu1 on 2021-08-03
I am so happy today! Well! Maybe! 

I hope I can help others too.

I had this problem in Windows and thought switching to ubuntu would solve the problem. It did not. It might be I was not able to find the right solution or messed up something else that prevented me to fix the problem.

However, as the title says, I saw a message that popped up as I was using Chrome:

"Network service discovery disabled. Your local network has a local domain which is not recommended and incompatible with the avahi network 
service discovery. It has been disabled."

So, I clicked it. And the fan stopped running. What just happened?

Is this a permanent fix or will I have to wait for such a message to pop up next time I boot up?

My fan is not running though (unless it is, but I cannot hear it). It is so quiet now. The temperature is going higher. It was 80 c..  It is up to 93 now on core 0 to 3. It has gone down to 90 now. Maybe it will work. Is it? I will post back.

---

### Post by Impavidus on 2021-08-03
If that's 90&#8304;C, it's really hot.

You clicked something that had nothing to do with power management or fan control, then the fan stopped. Now, it could be that clicking that button stopped some background process that used a lot of CPU time. When that stopped, the CPU cooling could stop too. Or it could be that your fan broke right when you clicked that button.

---

### Post by pierreu1 on 2021-08-03
Thanks! Good points! I will let you know unless the laptop melts. ;) The fan is at 900 rpm and core temp is 68 c and climbing slowly. I will boot out and see what happens.

---

### Post by Autodave on 2021-08-03
When was the last time you cleaned the fan?

---

### Post by pierreu1 on 2021-08-04
Thanks for the support.

I will let you know how my reboots go.

---

### Post by pierreu1 on 2021-08-04
Thanks for the help. 

I did, but that did not affect the noise at all.

---

### Post by dragonfly41 on 2021-08-04
Two separate ideas to try:

Install gkrellm as another monitor of temperature(s).

Install [tlp]("https://linrunner.de/tlp/") .. some write that it tames the fan.

[P.S.] A search for your message in post#1 found [this answer]("https://askubuntu.com/questions/339702/network-service-discovery-disabled-what-does-this-mean-for-me") (although old).

---

### Post by pierreu1 on 2021-08-05
THanks. 

You were right. I saw the same message this time and nothing happened. 

I did an experiment today. After reboot, the fan was not working at all. Noise zero. The temp app showed 0rpm. I disconnected wifi just after rebooting thinking that opening Chrome would get the fan to go mad which it usually does. I launched Libreoffice instead and it started the fan going mad (the cpu numbers went up of course). So, they are in sync. That is working. 

I am using chrome now (4 tabs) and the temp is stable at 60c (going done to 54c) on 4 cores and the fan rpm is 2700. The cpu is at 5% to 13% when I click the temp app. The fan is making the same constant whir now and so for half an hour. Is 2700rpm unusual? Is the temp too high? When I open more tabs, the cpu #s shot up and the fan too. So, the system is working to cool the computer. It is just very noisy.

Yesterday, I opened my computer and used a vacuum cleaner to suck any dust out the fan area. There was nothing much around it. But I will check again.

---

### Post by pierreu1 on 2021-08-05
This guy decided to tame his cpu: [https://www.youtube.com/watch?v=l-IfCgk-Uk4](https://www.youtube.com/watch?v=l-IfCgk-Uk4) which did tame the fan.

I think the temp monitor app I have is working. 

I see tlp has that capability to tame the cpu. I will try and let you know how good it worked. I hope I don't screw up! (I am 60 and a linguistics major. I guess programming is kind of related. LOL )

Thanks for the great ideas.

PS: I unscrewed the fan and everything was clean as a whistle. I have no idea on how the fan can actually cool anything the way it is. I will attach a pic if you are interested.

---

### Post by Autodave on 2021-08-05
60C is just fine....even up to 70C I wouldn't worry.

---


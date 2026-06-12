---
title: "Ubuntu and Virgin broadband"
date: 2006-12-13
forum: General Help
---

### Post by TheFlamingBush on 2006-12-13
Hi Ubuntu :)

i have recently moved over to the UK, and i was very happy with my Ubuntu Dapper os before moving here. I have since had to use XP in order to get online as ive been using AOL whilest trying to get broadband set up.

I have decided upon Virgin for the Broadband connection, and wondered if any others had also managed to get Ubuntu to work on the Virgin broadband. Im using a couple of Ubuntu boxes, having turned my new flatmate into a linux user since moving in. 

He had been using XP, but spilt tea on his keyboard laptop and that was the end of that. We got a usb keyboard, and plugged ubuntu into the box and voila!....instant operating system! ;)....quick fix for those suffering similar fates! :)

point is , now i have to ensure that we can use Ubuntu with the Virgin broadband connection, and im beginning to have my doubts, as i see that they do not offer any linux support with the broadband package. 

Can anyone assist me as to whether its possible to use Ubuntu through Virgin Broadband at all?....im not using the wireless connection just the usb modem that they supply.

Thankyou. :)

---

### Post by laidback on 2006-12-15
For information, yes I have managed to get Ubuntu to work with Virgin. A friend of mine has been persuaded by myself to give Ubuntu a try, he also uses XP with Virgin. Initially it was really slow but after some adjustments in the DNS tab of Networking it just flew along. We achieved 450kb/s dowload speeds with the Ubuntu updates. He has a 2 MB connection. All I can manage on my 512 Kb connection is 50-60 kb/s at best. After installing Dapper 6.06 I spent an hour or two applying the updates to my system, on his machine it took just 4 mins 18 secs; fantastic. We have tried wireless but gave up. I want success and this seemed to be streaching a point. Ubuntu did the install for the network connections all I did was delete a reference in the DNS tab to his router. Unfortunately it seems to reappear from time to time so something else is going on as well, but with a little edit after each boot up the system works very well. Faster than with XP in fact. As I don't visit his house too often I have to wait until I can review his system and check out the latest problems, in the meantime he is quite happy to edit the DNS tab as above. 

When I was choosing a service I checked with them as to whether Linux was supported/allowed. Few appear to, which is odd since I'm led to believe that loads of them run Linux/Apache servers!

---

### Post by TheFlamingBush on 2006-12-19
> **laidback said:**
> For information, yes I have managed to get Ubuntu to work with Virgin. A friend of mine has been persuaded by myself to give Ubuntu a try, he also uses XP with Virgin. Initially it was really slow but after some adjustments in the DNS tab of Networking it just flew along. We achieved 450kb/s dowload speeds with the Ubuntu updates. He has a 2 MB connection. All I can manage on my 512 Kb connection is 50-60 kb/s at best. After installing Dapper 6.06 I spent an hour or two applying the updates to my system, on his machine it took just 4 mins 18 secs; fantastic. We have tried wireless but gave up. I want success and this seemed to be streaching a point. Ubuntu did the install for the network connections all I did was delete a reference in the DNS tab to his router. Unfortunately it seems to reappear from time to time so something else is going on as well, but with a little edit after each boot up the system works very well. Faster than with XP in fact. As I don't visit his house too often I have to wait until I can review his system and check out the latest problems, in the meantime he is quite happy to edit the DNS tab as above. 

When I was choosing a service I checked with them as to whether Linux was supported/allowed. Few appear to, which is odd since I'm led to believe that loads of them run Linux/Apache servers!

well thats great news, laidback....im about to test out whether i can get ubuntu to work with my connection. today's the day.....
was there anything special that you had to do when you got the virgin modem and cd?.....just wondering?....or was it a straight install situation?, with doze of course it is an autoset up. 

what reconfig did you have to do with the DNS, ie the deletion of the reference?.....im not sitting behind a router at present, although i will be getting my own router over in a week or so, so this should make the situation a whole lot better, and secure of course;)

any others who have similar situations?

---

### Post by laidback on 2006-12-27
Initially I just let Ubuntu do its thing, i.e. default connection. Under DHCP style the performance was not good, so I switched it to DNS. However, each time you boot up the address of the router reappears ahead of the DNS address, this slows things down. Delete this address and off it goes. I have yet to return to my friends house to spend more time on this remaining issue so at present he simply boots up and deletes this odd address before surfing. So far it has worked every time, he's really pleased with the results. Ideally he needs to use DHCP as this is the standard system for Virgin and XP. For Linux I didn't use any Virgin discs, just the Ubuntu one for standard installation, V6.06 Dapper Drake. How did I know the DNS address for Virgin since they don't issue any?, I didn't and don't, when I switched to DNS addressing from DHCP an address simply appeared in the right place, I assumed that this is correct and would work, it does.

Hope this helps

Laidback

---

### Post by jeremy on 2006-12-28
> **laidback said:**
> We achieved 450kb/s download speeds with the Ubuntu updates. He has a 2 MB connection.
Could you please tell me how you achieved this, I have a 3MB connection, and can only achieve slightly over 300KB/s downloads (as expected). Following your method I should be able to dl at about 675KB/s!

---

### Post by laidback on 2006-12-28
Jeremy,

I can't tell you much more than what's above. Like you I'm astonished at the performance of my friends connection. He has a 2Mb broadband at present, going up to 8Mb soon. He uses Virgin with XP as his standard system. Even that's fast but I cannot give figures. The 450kb/s quoted is taken from the splash screen that appears when you download from the mirror sites, it is the best, for a large download it will decay to about 350-375kb/s towards the end, I have seen as low as 250kb/s but this seems unusual. I did some simple sums to compare his with mine on the large (>200Mb) download when we firsts installed his system and went to the mirrors to update the installation. I know it took my system well over an hour just to download the files, with his it was completed within minutes, I could hardly believe it, in fact I doubted that it had worked successfully, but it has. The time seemed sensible for the speed of connection and size of download. 

It could be that his connection is already up to 8Mb but he hasn't been informed and doesn't yet have to pay for it. 

We can only get this performance with the DNS connection, using static ip addresses, go over to DHCP and it slows down to an unacceptable crawl. It was this terrible performance that prompted us to mess with the system. It was so bad that my friend was on the point of giving up Ubuntu and Linux in favour of XP, not so now!

The system has been running for several weeks and continues to perform well. Indeed we spoke this very morning and again he remarked on the performance of his connection, even when compared to XP which is using the same hardware as it's a dual boot arrangement. He reported that the Internet was virtually instantaneous but then it is the Christmas holidays this week.

Sorry I can't be more informative, these comms systems are just black boxes to me, I'd love to get this performance on my own machine, even a proportion of it will do as long as it's over the 50-60 kb/s that I enjoy. I've tried the DNS address at home, it works but not as quickly as my normal addresses.

Happy New Year
Laidback

---

### Post by TheFlamingBush on 2007-05-19
i cant believe it but ive had to use myXP for the last 4 months, as i gave up trying to get an internet connection with Ubuntu using the virgin modem. Im now unbelievably sick to death of XP, and have decided to re-enter the fray of trying to get an internet connection with Ubuntu.....i still have the same virgin ISDN speedtouch USB ADSL. ppp modem.....

all assistance greatfully appreciated....im a Linux newbie!.....although i have been using it for almost all my personal work during that time, so it sure would be nice to use it to communicate over the net! :-/

---

### Post by TheFlamingBush on 2007-06-03
found the answer!..........or more likely steve haper did, so all those using speedtouch modems now have no problem connecting in one clean swift motion! 

this guy is the bomb!!!!

[http://http://www.squeezedonkey.com/wiki/linux/index.php?title=Instructions_Here]("http://http://www.squeezedonkey.com/wiki/linux/index.php?title=Instructions_Here")

---

### Post by BigSilly on 2007-06-03
For original poster's peace of mind, I too use Virgin Broadband here in the UK on my Ubuntu system. I have a 2meg connection, and all is well.

EDIT: Sorry, didn't see you had posted this a while ago!

---


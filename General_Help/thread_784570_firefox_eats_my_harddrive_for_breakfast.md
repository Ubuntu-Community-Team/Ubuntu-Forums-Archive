---
title: "firefox eats my harddrive for breakfast"
date: 2008-05-06
forum: General Help
---

### Post by SpaceTeddy on 2008-05-06
Hi Folks,

i ran into a problem today which i am not sure if this is a distro or firefox specific problem. The reason why i am not sure is that i have noticed a huge increase in harddisk activity since i switched over to hardy. seriously, in gutsy, my comp used to use the hd when it booted - pretty much never after that. Now, i get random hd-frenzies from time to time... but that is besides the point (btw. i have no swap, 2G RAM and according to the little sysmon thingy there was never, ever any time when i had more than 40% of my ram used activly - NEVER !)

On to my problem: i used different firefox profiles for different proxy configurations. lets say i have five profiles... default, p1, p2, p3, p4. I usually use default, only for debugging purposes i sometimes start the other profiles. It used to be the cast that i could run all of these profiles at the same time (even last week it still worked), but today, if i try to load more than three profiles at one time, my harddrive goes crazy - and i mean crazy. Both CPU's are doing 100% hd work. Everything goes slow, the firefox windows don't react anymore. As if it is trying to kill my harddrive. 
However, if i only run three profiles, i get semi-regular harddrive action - with two or one profile there is no access to the hd at all.
what strikes me odd is that this only happens now, and only with more than three profiles... 

Also, i let the thing run thinking it's doing some updates or something. Let them do their work for about 30 minutes (constant HD-activity). Using top, i found out that the load on my system was at around 9 (9.47 9.01 9.34). That is way too high for my comp. The only other time when i managed to get it this high was when installing four Virtual machines at the same time...

So, anybody any idea what could be causing this ?

---

### Post by tardomatic on 2008-05-06
Hi,

Check on top and see if trackerd is running. I had a similar problem with hard drive access and it turns out that trackerd is updating its indexes every now and then... I eventually uninstalled it because disabling it using the Sessions/Services tools didn't stop it.

Just a thought

---

### Post by sports fan Matt on 2008-05-06
The hard drive must be hungry..:lolflag:

---

### Post by tardomatic on 2008-05-06
Or better yet: [http://ubuntuforums.org/showpost.php?p=4770985&postcount=50](http://ubuntuforums.org/showpost.php?p=4770985&postcount=50) (From the sticky)

---

### Post by davidpbrown on 2008-05-06
I had similar and spotted the tracker was set to index file contents - undoing that helped.

-> System::Preferences::Searching and Indexing::Files and untick 'Index file contents'


But also there seems to be large hard drives use relating to a Firefox problem.. I try scrolling down and frequently it seizes up for a few seconds.

---

### Post by davidpbrown on 2008-05-06
> **tardomatic said:**
> Or better yet: [http://ubuntuforums.org/showpost.php?p=4770985&postcount=50](http://ubuntuforums.org/showpost.php?p=4770985&postcount=50) (From the sticky)

Which bug report was that? Would be interesting to read.

---

### Post by davidpbrown on 2008-05-06
See also thread [http://ubuntuforums.org/showthread.php?t=784555](http://ubuntuforums.org/showthread.php?t=784555)
which suggests the bug is well known and being dealt with.

---

### Post by tardomatic on 2008-05-06
i think this one: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728)

---

### Post by SpaceTeddy on 2008-05-07
thanks for the info, guys. Seems like this was a tracker problem. Once i killed tracker (console: killall trackerd) the windows suddently load normal and do not cause a hd-frenzy. 
Makes we wonder tho, i had set the tracker on "stop indexing" via the little tracker symbol... why it still indexed is beyond me. Ah well, killed it, and it seems to work now.

Thanks again everyone :)

---

### Post by vanadium on 2008-05-07
It is a firefox bug. You can work around it as following. Credit goes to Pjotr, who maintains a Dutch site ([http://computertip.googlepages.com/enkelebekendefouteninubuntu):](http://computertip.googlepages.com/enkelebekendefouteninubuntu):)

1) edit - preferences - security: disable the two security options "Tell me if a site is ..."
2) Close Firefox
3) Delete the files urlclassifier3.sqlite and urlclassifier3.sqlite-journal (the latter might not be present). These files are in the root directory of your firefox profile. To access it in Nautilus, press Ctrl+a to show the hidden directory and navigate to a directory such as
.mozilla/firefox/v5593730ffghgzm.default/
(the last part is different for each user).

Once the bugs are fixed, just re-enable these security features.

---

### Post by SpaceTeddy on 2008-05-07
thanks - that fixed it proerply... i can now run the different profiles without hassles... 

thanks again

---

### Post by vanadium on 2008-05-07
I just learned from our terrific Dutch forum that the issue is fixed, and we should receive an update soon. The feature nevertheless remains a resource intensive feature, so you may want to leave the settings off on less powerfull computers.

---


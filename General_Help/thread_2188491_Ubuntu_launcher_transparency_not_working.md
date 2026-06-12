---
title: "Ubuntu launcher transparency not working"
date: 2013-11-17
forum: General Help
---

### Post by agale031176 on 2013-11-17
I have updated to the latest 13.10 and the Ubuntu launcher on hide it still shows the launcher background as you can see in the attachment. Did anyone experience this? Or can suggest what to look for to sort this out?

[ATTACH=CONFIG]247902[/ATTACH]

---

### Post by grier-devon on 2013-11-17
I am assuming you did a upgrade vs fresh install? I usually have had a decent luck with updating as long as I do it the within the week of the release. Otherwise I always do a fresh install.

Try using Unity Tweaks from the software center and see if you can get you bar back.

---

### Post by agale031176 on 2013-11-18
Yes I did an upgrade not a fresh install and tried unity tweaks but still no luck. I think the issue is with bumblebee as I have an Optimus graphics card. This worked before on 13.04 but during the upgrade something went wrong. Also tried reinstalling the bumblebee but no success still.  I would like to do a fresh install but I have too many important things saved in the HD. If I don't manage to sort it out I try to backup things and do a fresh install.

In the meantime if anyone has any other suggestions to try I would appreciate to avoid doing a fresh install.

---

### Post by grier-devon on 2013-11-18
Sorry to hear, if I may recommend starting to consider either A, using cloud services so you can setup to sync the locations in which you store you important work or have a dedicated external HDD hooked up to the computer which will back up where you store you work regularly. I know this doesn't fix the problem right now and I wish I had another answer for you but this will solve the problems for future upgrades/fresh install.

I did find this, it is 12.04 but hell see if this fixes your problem especially if no one else has anything to suggest, best of luck...
  [http://askubuntu.com/questions/214529/unity-launcher-has-disappeared](http://askubuntu.com/questions/214529/unity-launcher-has-disappeared)

---

### Post by grahammechanical on 2013-11-18
Do the graphics seem to run a bit slow? Ubuntu has a fallback video mode called llvmpipe. It is a subset of the Nouveau open source video driver for hardware that does not provide accelerated graphics. And that is what is causing that effect. As you have guessed, this is a video driver issue. I think that Ubuntu is running llvmpipe as a fallback.

Have you seen this? 

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

Oh, by the way, I experience that when I run Recovery Mode>Resume from the Grub menu. 

Regards.

---

### Post by agale031176 on 2013-11-18
Thanks everyone for your help.

@[COLOR=#000000]grahammechanical you hit the nail on the head. It was using the fallback video mode llvmpipe. Followed the link [/COLOR][http://www.webupd8.org/2013/08/using...vers-with.html]("http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html") you posted and it seems to have sorted it out.

Now all is back to normal but I would sync important file to Ubuntu One.

---


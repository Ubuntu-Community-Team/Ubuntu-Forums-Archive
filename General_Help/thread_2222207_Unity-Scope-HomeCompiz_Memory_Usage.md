---
title: "Unity-Scope-Home/Compiz Memory Usage"
date: 2014-05-05
forum: General Help
---

### Post by speartip on 2014-05-05
This was a problem I 1st noticed while using the Beta of 14.04.
I have since installed the final iso, but my problem still persists.
After searching using the Dash, Compiz & Unity-scope-home memory usage goes sky high, as the attachment shows, & only a logout or reboot, brings it back down to normal levels.
I have searched the forum & googled the problem, but no-one else seems to have this issue.
Any ideas friends?
[ATTACH=CONFIG]252892[/ATTACH]

---

### Post by lilyrivers48 on 2014-05-09
I'm having this too, up to 100mb memory usage by compiz and it starts to freeze things. I've installed the latest kernel and even that didn't fix it.

Not even much is open and i'm suspecting that its a problem with the intel stuff.

---

### Post by Frogs Hair on 2014-05-09
I'm seeing in the mid 30's for compiz alone with the ccsm installed and am using the default nouveau driver. I installed the release candidate on both my computers a day apart and just prior to the final. AMD 64 2.8 Ghz. with Nvidia grapics on this computer Intel i5 with integrated graphics on the other.  Searching with dash while runing the top command in the terminal shows no real increase , but online search is disabled and I don't know if that has an impact.

---

### Post by speartip on 2014-05-10
Thanks for your replies.
Frogs Hair.. I too disabled the online search, I also disabled the scopes that I do not use, but the problem persists.
Compiz starts at about 60mb. If I open the dash it goes up to between 70-80mb. But if I open the music the Unity Music lens/scope, I get the issue in my 1st post.
 There does seem to be a corelation between how much Unity has to search through. For eg. If I open the Pictures Scope, I have about 300 pictures, & compiz goes upto about 160mb, then if I open the Music scope were I have about 17,000 songs, Compiz goes upto about 800mb.
 I could disable those scopes but then Unity is useless really.
Any other input would be appreciated.

Lilyrivers48... I wish mine would only use 100mb. I don't know your specs, but I don't think 100mb is overly excessive.

---

### Post by PJs Ronin on 2014-05-10
This got me to thinking, so I compared my conky data with System Monitor and came up with this:

[ATTACH=CONFIG]253050[/ATTACH]

I have no explanation why the difference, but it is substantial.

---

### Post by speartip on 2014-10-21
I thought I would readdress this thread as 14.04 has now been out 6 months & this issue still persists for me.
The problem seems to be the amount of files unity needs to search through, if your video, music, photos files are only small you will have no problem. However if you have thousands of songs, pictures, videos etc.. then the minute you open the lens in the unity dash, compiz & unity-scope-home just eat up memory.
My only workaround for anyone else having this problem is to uninstall all the unity-scopes/lenses that are causing the problem.
I have deleted them all except unity-lens-files, unity-lens-applications, unity-scope-home, & unity-scopes-master-default. 
My system seems to have settled down, with compiz using less than 200mb & unity-scope-home only using 5mb instead of upto 500mb before.
I got the idea from here:
[http://askubuntu.com/questions/368406/unable-to-remove-some-unity-lenses](http://askubuntu.com/questions/368406/unable-to-remove-some-unity-lenses)
2nd post.
Hope this helps someone.

---

### Post by mc4man on 2014-10-21
Probably something they should have addressed, unlikely now.  (maybe I'll look/file a bug anyway.
Myself  I do remove many of the unused scopes (or disable via Applications > Dash plugins) & generally use around 80mb unless I expand the 'Installed' in the applications lens which then bumps up about 1mb per entry.

Here because I've more than 1 music player with a scope installed the music lens is somewhat worthless anyway as there is no source filter anymore (another [bug never really addressed]("https://bugs.launchpad.net/unity-lens-music/+bug/1189038")
People with modern machines (4Gb+ ram) are likely unaffected by compiz's mem use, you have it so may as well use it.

---

### Post by speartip on 2014-12-04
A recent Compiz update seems to have reduced Compiz memory usage significantly.
Good to see these matters still being addressed.
I will wait a while, and if all is well, marked this thread as solved.

---

### Post by speartip on 2015-01-27
Although the update mentioned above seems to have reduced compiz memory usage, it still regularly topped 250mb.
Now heres the strange thing. About a week ago I changed my icon theme to RAVEfinity's Vibrancy-Full-Dark-Orange theme, the ppa can be got here:
[https://launchpad.net/~ravefinity-project/+archive/ubuntu/ppa](https://launchpad.net/~ravefinity-project/+archive/ubuntu/ppa)
Since doing this my compiz memory usage has not gone above 50mb. No idea how this could be, but i'm happy & now marking this thread as solved.

---


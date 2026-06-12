---
title: "Stability issues"
date: 2008-05-25
forum: General Help
---

### Post by chicobo329 on 2008-05-25
Lately I've been having some stability issues with my 8.04. I'm running on the 2.6.20 kernel (my Broadcom wireless doesn't seem to be detected in anything higher).

In some programs, usually Firefox, that show a 'Save File' dialog box, sometimes that program will spontaneously shut down with no warning. This usually happens in Firefox when I go to save images, regardless of the webpage. This also happens if I visit sites with video such as Youtube and the like.

There's also instances where Firefox completely locks up randomly, again with no warning, and it doesn't want to shut down. Force quitting the program runs a risk of everything just deciding not the work. Sometimes after the Force Quit, the sound is shut off, the Shut Down window does not show up (in fact, clicking the button on the top freezes the entire top taskbar), and various programs decide to not load anymore, such as Firefox and Archive Manager. Checking the Processes in the System Manager shows that they are sleeping in the background but do not actually show up to me. I can click Firefox multiple times and it creates multiple sleeping processes. I have to do a complete restart to fix all of this (Ctrl + Alt + Backspace, then click Shutdown -> Restart at the login screen).

My version of Firefox is 3 Beta 5. I have all the other latest updates for my programs. How can I fix these strange problems?

---

### Post by malachi1990 on 2008-05-25
I had a similar problem when I first started using hardy.  For some reason, hardy doesn't like to play nice with the older kernels, in my experience (I've installed it on a desktop and a laptop).  As for your broadcomm wireless, there are several options, the best of which I believe is getting the ndiswrapper to use your windows wireless drivers with it (again speaking from personal experience).

The broadcomm stuff I used came from here:
[http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcomm](http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcomm)

From there, you should be able to configure for any network you come across.

Hope this helps.

---

### Post by MaindotC on 2008-05-25
I think what would really be best is if you start over with a nice, fresh, clean install.

---

### Post by chicobo329 on 2008-05-26
I guess I'll have to do a reinstall, I still have a myriad of other little strange issues (X Server won't complete its configuration process, thus my Nvidia video card doesn't work is my other big one). A bit disappointing I have to do that though.

I saved the Broadcomm link for when I reinstall.

---

### Post by chicobo329 on 2008-05-26
Sorry for the double post.

I reinstalled and my graphics card is now detected and Broadcom now works too after checking a couple of howtos.

However Firefox Beta 5 is still very unstable and will not be responsive at any time, especially when loading a new page. It won't spontanously shut down when saving images, but it will randomly lock up or lag after a while. It's very strange...

---

### Post by MaindotC on 2008-05-27
I suggest you get rid of the new Firefox unless  you have any interest in providing your bug reports to launchpad.  I'm still using Gutsy till 8.04 is a little more stable.  I have a lab machine at school that I have 8.04 installed and I use it as my test bed to see what the latest updates and fixes are like.  So far it hasn't been too promising :(

---


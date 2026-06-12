---
title: "Help me please I am going insane. Fonts are driving me maddddd!"
date: 2016-12-19
forum: General Help
---

### Post by harley.four20 on 2016-12-19
So I recently upgraded to ubuntu 16.04, and after I did for some reason my fonts have gone haywire. So far what I have noticed is when I am in chrome (my main browser) or in firefox (my secondary browser) all the base fonts have gone from regular font to "MetallicA OLD" and possibly more. This is a bad scenario as the metallica font only has the letters m,e,t,a,l,i, and c in the different font, so its just a garble of font. I have looked in the settings for both chrome and firefox and nothing there seems out of the ordinary, and I have specifically made my fonts custom to a regular font, but they still remain the same metallica font. I have tried to locate the actual font in my computer to erase it but cant find it in any file. I downloaded "font manager" and it only picks up about one 10th of the fonts in my computer and it wont let me pick my "computer" drive file to find fonts in every possible area. So that program is not helping. I cannot read my browsers properly. This is starting to make me go crazy. What do I do. Please help me!

side note: I am not good with script, pretty much need to be walked thru every bit of it.

I have maybe discovered that the serif and sans serif have maybe been taken over by these other fonts if that helps?

I tried attaching a screenshot of how this all looks to me, hopefully that worked.

[ATTACH=CONFIG]272771[/ATTACH]

edit: when upgrading I did choose this option on my uploading process. I wasnt sure what to select and my computer friend who usually helps me with this stuff wasnt available.
[ATTACH=CONFIG]272772[/ATTACH]

---

### Post by howefield on 2016-12-20
Is it just the browsers that are affected, the system fonts are ok ?

---

### Post by speartip on 2016-12-20
You could try deleting the fontconfig folder in /home/.confg. Logout & in again, see if that helps.

---

### Post by harley.four20 on 2016-12-23
Ive discovered that it is my arial font. it has been replaced somehow

---

### Post by harley.four20 on 2016-12-23
will deleating the font config file have any adverse reactions?

---

### Post by speartip on 2016-12-23
> **harley.four20 said:**
> will deleating the font config file have any adverse reactions?
No it will just rebuild itself again the next time you login.

---

### Post by harley.four20 on 2016-12-26
> **speartip said:**
> You could try deleting the fontconfig folder in /home/.confg. Logout & in again, see if that helps.

So I went into my home folder and then into my .config folder. So Im at /home/.config . Now in that folder, I dont have a fontconfig folder. I have a fontgroups.xml file or I have a folder titled Font-manager. Now I downloaded a font manager app from the software center, it did not locate most of my fonts unfortunately, it was of little use. So is this the folder you are referring to or is it the folder related to the app I downloaded. Inside the font-manager folder I have one folder titled conf.d and three files titled directories.conf, preferences.ini, and select.conf. and inside the conf.d file there is no files or folders. please advise

---

### Post by speartip on 2016-12-26
Sorry my mistake. It's in the home/.cache folder.

---

### Post by harley.four20 on 2017-01-19
> **speartip said:**
> Sorry my mistake. It's in the home/.cache folder.

[COLOR=#1D2129][FONT=Helvetica]So i tried removing the cache folder and it did not solve the problem. Sorry for the late reply, I have been without internet for a while. what do I do now?[/FONT][/COLOR]

---


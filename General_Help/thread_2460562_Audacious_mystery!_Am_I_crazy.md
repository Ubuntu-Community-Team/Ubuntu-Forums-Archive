---
title: "Audacious mystery! Am I crazy?"
date: 2021-04-13
forum: General Help
---

### Post by ishmael3 on 2021-04-13
Any explanation for this? I'm kinda spooked!
 
 I have two desktop computers. I have been using 20.04 on the first one for a month and am happy with it. I am now setting up the second machine, which I want to be just like the first, in appearance, behavior and installed apps.
 
 So I installed the OS on the second machine from the same live USB as for the first machine. On the second machine I have so far set up ONLY the first user account (the administrative acct), and begun installing the software I will need. I have not  yet transferred any personal files to the second machine.  
 
 So, yesterday I download "Audacious," a basic, light-weight media player, using the Gnome Software GUI. After it finishes installing I open it to check the preferred settings. And I am totally freaked out because I see, in the list that shows recently played files, an MP3 file that I played to on the OTHER MACHINE several days ago!  
 
 In other words, this is a virgin installation of Ubuntu, and a virgin installation of Audacious. How could Audacious on the second machine even know that file existed?? And when I rt-click the title for more information it shows the path to that file ON THE OTHER MACHINE --  though it happens to be the wrong path and the wrong title because I changed both those things after I played it on the first machine!!  
 
 There is no networking (verified in Files > Other Locations), and no sharing between the two machines. They are intended to be as isolated as possible. The only thing in common is they are both wire-connected to the same router.  
 
 It's past April Fool's, and I am not making this up. Please... what am I missing here?

---

### Post by Impavidus on 2021-04-13
It appears the computer already guessed you want it to be the same as the other.

This information could be transferred by a livedisk with persistence, but should only transfer it from a live session on the first computer to a live session on the second, not between the installed systems. Or it could happen if your home directory is on some network storage used by both computers, but then the path should be accurate. And you would know if you set that up.

---

### Post by ishmael3 on 2021-04-21
Duh!  
 
 I woke up about 2am realizing it was the .config folder! I transferred that whole folder from first machine -- INCLUDING an "audacious" folder within -- prior to downloading the app.
 
 So, not quite a "virgin" installation after all. I'm not crazy, just oblivious.

---

### Post by CelticWarrior on 2021-04-21
A very "duh" moment, indeed.
Don't worry, we all have had those.

---

### Post by uRock on 2021-04-21
I can see how that'd be scary. Glad you can feel secure on your computer, again.

---


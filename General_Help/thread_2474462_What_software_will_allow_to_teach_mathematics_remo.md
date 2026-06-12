---
title: "What software will allow to teach mathematics remotely?"
date: 2022-04-30
forum: General Help
---

### Post by papajooj on 2022-04-30
Kubuntu 21.10  

There is a 9th grader student, who got in a hospital. He will take 4 exams in a month, but he can't prepare there. He only has an android smartphone in a hospital.  

I need to install software on my desktop computer that: 
1. Allows me to draw the simplest geometric shapes and write text (as if it were a regular algebra / geometry notebook). 
2. Captures the sound and picture from my PC screen and transfers it to his smartphone, and in response to me, the sound from his smartphone. 

What programs do you recommend?

---

### Post by dragonfly41 on 2022-04-30
Some ideas ..

4 months is a short time and you need to get underway quickly.

Recently I have been studying remote learning tools and api's and for your case one option (which I have not tried) would be for teacher (you) and student to share a moodle.org account.

To get started you can install on your desktop.

sudo apt install geogebra
sudo apt install geogebra-gnome

Then create a moodle.org account for you and student.

Then add a geogebra plugin

[https://moodle.org/plugins/mod_geogebra](https://moodle.org/plugins/mod_geogebra)

Regarding playing Sound

[https://wiki.geogebra.org/en/PlaySound_Command](https://wiki.geogebra.org/en/PlaySound_Command)

.....

An easier shared use of geogebra is here (you will need a monthly Premium account to play with it as team).

[https://www.rollapp.com/app/geogebra](https://www.rollapp.com/app/geogebra)

.....

For more advanced maths you can share a Wolfram account.

[https://community.wolfram.com/search?p_p_id=search_WAR_searchportlet&p_p_lifecycle=0&p_p_col_pos=3&p_p_col_count=4&_search_WAR_searchportlet_filter=&_search_WAR_searchportlet_start=0&_search_WAR_searchportlet_limit=20&_search_WAR_searchportlet_mvcPath=%2Fsearch.jsp&keywords=geometry](https://community.wolfram.com/search?p_p_id=search_WAR_searchportlet&p_p_lifecycle=0&p_p_col_pos=3&p_p_col_count=4&_search_WAR_searchportlet_filter=&_search_WAR_searchportlet_start=0&_search_WAR_searchportlet_limit=20&_search_WAR_searchportlet_mvcPath=%2Fsearch.jsp&keywords=geometry)


[https://stackoverflow.com/questions/8748294/simple-programming-techniques-tricks-in-mathematica-for-making-graphics-for-th](https://stackoverflow.com/questions/8748294/simple-programming-techniques-tricks-in-mathematica-for-making-graphics-for-th)

.....

If you only want to draw really simple shapes then look at boxysvg.
Or svgedit.

---

### Post by TheFu on 2022-04-30
I wouldn't use anything except Jitsi **meet.jit.si/<make up a tag>**   for the shared desktop/window with the student. This is a website accessed using a browser window. There's an Android client available. No logins needed.  Just agree on the URL to meet at (make it unique to keep the riff-raff out). Go there using any WebRTC enabled web browser. I use chromium running in a constrained environment, but the other people at the meetings use firefox, chrome, brave, and other huge, bloated, browsers.

As for math programs, there are many. AlternativeTo.net should be helpful in getting leads based on programs you already know.  Back when I was cleaning basic maths at University, there was a commercial program called MathCad.  It is a symbolic calculator with symbols and graphing like a professor would show on the chalkboard - just more readable. I'd be surprised if a F/LOSS version of that program isn't available.  Ok - just did a bit of research. MathCAD was bought by MatLAB, which is more of an engineering tool.  But found some one that said SMath was an alternative: [https://en.smath.com/view/SMathStudio/summary](https://en.smath.com/view/SMathStudio/summary)  It isn't F/LOSS, but it is freeware with a Linux version. I've never used it.
Also saw there is a LibreOffice addon to enter equations. **LibreOffice Math** has an equation editor. This seems to be just to make pretty equations - no calculations are behind the equations that I can see.

Or you could use almost any USB drawing tablet with a paint program. Just look for a USB drawing tablet that uses generic drivers so it works on Linux. Be careful picking the tablet, since many won't work with Linux. Some names (found in an article) GAOMON Huion Wacom. Don't assume all models support Linux.

BTW, 21.10 support ends in July, so before you go to much effort to get this working, I'd move the Kubuntu 22.04 which is an LTS release that will have **support for** the next **3 yrs**.  
[https://wiki.ubuntu.com/JammyJellyfish/ReleaseNotes/Kubuntu](https://wiki.ubuntu.com/JammyJellyfish/ReleaseNotes/Kubuntu) 
[https://kubuntu.org/news/kubuntu-22-04-lts-released/](https://kubuntu.org/news/kubuntu-22-04-lts-released/)

I'd really push to get the student a larger tablet, btw.  A $60 amazon 8in tablet isn't THAT much larger, but so much more can go on the screen.  I have a 2017 model for reading websites, ebooks, PDFs, streaming content, it is fantastic, especially for the price. It is good enough for audio too - stereo, but not too loud. It has a 2.5mm audio jack.
With a BT keyboard and going through a website, it could be used to create documents.  OTOH, a cheap 11inch chromebook would be better for almost any student. Those can be $99 new or $75 used.  Chromebooks are what most students in my school system use - that's about 120K students, BTW. There's a huge school software industry for chromebooks since many millions of students across the country use them now. [https://www.educatorstechnology.com/2015/02/10-of-best-chrome-apps-for-math-teachers.html](https://www.educatorstechnology.com/2015/02/10-of-best-chrome-apps-for-math-teachers.html) I searched for "Chromebook math school software" There seem to be many, many, many, options.  Our school system gives chromebooks to each student.  They are expected to use the same device for 3 yrs. It has leveled the computer field so lower-income students aren't disadvantaged compared to very high income students, at least in having a specific computer. All the software used/expected is provided and works with chromebooks.

And don't forget that most physical calculators have been converted to Android apps.  My HP-15c from University is available, as are most models of the HP-41.  Those also exist for Linux, so you both can use the same model. I bet some Casio and Ti calculators (I'm way out of touch here) are available too.

---


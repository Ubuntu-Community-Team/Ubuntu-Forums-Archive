---
title: "Problems with 16.04"
date: 2017-03-11
forum: General Help
---

### Post by Gstrazds on 2017-03-11
My 16.4 just went crazy! Saturday, March 11, 2017

all of the ubuntu updaters / software installers stopped working! synaptic, software installer, and the Ubuntu update installer, terminal. Dameon collapsed; core dump

glenn@glenn-Satellite-C655D:~$ lsb_release -a 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial

Went back to kernel... 63 then re-updated; The updaters work again;  [COLOR=#333333][FONT=UbuntuMono]dconf-editor does not populate????
It's better for stability than it was; It also will not be fixed till it's fixed.. So we can hurry up and wait.
you may have a different opinion.

[/FONT][/COLOR]

---

### Post by Bucky Ball on 2017-03-11
@Gstrazds: My three machines.

Linux tosh 4.4.0-64-generic #85-Ubuntu SMP Mon Feb 20 11:50:30 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

No issues on any of them. It is not a problem with the stability of a release if you are the only one with the issue. Have you seen anyone else with the same issues? :)

I suggest you post a support thread about your problem and see if you can't get it sorted out rather than 'hurry up and wait' (unless you can establish that this is a problem shared by others en masse after update to kernel .64, of course).

---

### Post by Gstrazds on 2017-03-13
[COLOR=#000000]> 

I suggest you post a support thread about your problem and see if you can't get it sorted out rather than 'hurry up and wait' (unless you can establish that this is a problem shared by others en masse after update to kernel .64, of course).[/COLOR]

It was a general comment. How many times do you have to click on the Send problem report before if feels generally unstable. The latest round of Send problem reports resulted from the above and saved it by back leveling then re-installing the updates... 

I can tell when the bug reporter sends back updates which indicate the number of users that have the same problem. like a lot of them; or not a lot of them. 

Actually, you did not comment on the core dump.

I wanted more updates So I hit the update button; Waiting is sometimes better - I would have bypassed the Core Dump problem. 

You have three perfectly working machines - You possibly have time on your hands; helping is helpful.

---

### Post by Bucky Ball on 2017-03-13
> **Gstrazds said:**
> 
You have three perfectly working machines - You possibly have time on your hands; helping is helpful.

Firstly, this isn't a support thread. Secondly, it isn't your thread to ask for support, so why are you? Post a new thread in a support area if you want support and more than happy to help. I spend a lot of time helping others here and have done for the last nine years (in fact, I was once a staff member as I spend that much time helping people here).

And you? You have been here for not quite two years less than me, and have 45 posts. I think I have somewhere between 12,000-15,000 (I haven't looked at my post count in ages). :)

---

### Post by QIII on 2017-03-13
Posts moved from chat area to General Help.

---

### Post by ian-weisser on 2017-03-13
> **Gstrazds said:**
> 
all of the ubuntu updaters / software installers stopped working! synaptic, software installer, and the Ubuntu update installer, terminal. Dameon collapsed; core dump

[...]

Went back to kernel... 63 then re-updated; The updaters work again;  [COLOR=#333333][FONT=UbuntuMono]dconf-editor does not populate????
It's better for stability than it was; It also will not be fixed till it's fixed.. So we can hurry up and wait.
you may have a different opinion.[/FONT][/COLOR]

A bit more detail would be helpful. The dconf editor in my 16.04 test system seems fine. Any suggestions on how we can duplicate your issues?

---

### Post by Gstrazds on 2017-03-17
Well, thank you for your response...   Yes, System works great; Ubuntu 4.4.0-67.88-generic 4.4.49.. loaded in a new Chrome today - more fluid; I seem to have more battery life? 

Enclosed, a screen shot of the deconf editor. click on the directories - nothing happens; nothing populates.

If suggestions were available to test the problem I would happy to try them... Well the add image url idea is not working 
So you can see the image at the below url.
[https://www.facebook.com/photo.php?fbid=1512451145432889&set=a.108253219186029.14451.100000040558111&type=3&theater](https://www.facebook.com/photo.php?fbid=1512451145432889&set=a.108253219186029.14451.100000040558111&type=3&theater)

Thanks

---

### Post by vasa1 on 2017-03-17
> **Gstrazds said:**
> ... Well the add image url idea is not working ...
What about clicking on the paper clip icon which will open a window allowing you to choose a file to upload? People may find viewing images hosted on the forum more convenient than visiting some external site.

---

### Post by Gstrazds on 2017-03-17
> [COLOR=#000000]What about clicking on the paper clip icon which will open a window allowing you to choose a file to upload? People may find viewing images hosted on the forum more convenient than visiting some external site.[/COLOR][COLOR=#000000]


So it's done... thanks[/COLOR]

---

### Post by deadflowr on 2017-03-17
Are you clicking on the tinny tiny arrow to expand the dconf listings?
Highlighting the dconf listing does nothing but highlight the listing.
It won't expand anything.

---

### Post by Gstrazds on 2017-03-19
> **deadflowr said:**
> Are you clicking on the tinny tiny arrow to expand the dconf listings?
Highlighting the dconf listing does nothing but highlight the listing.
It won't expand anything.

tried that - works;

Since the front page is blank - one could put a headline; Dconf editor with a direction to click on the arrows to navigate the app.

thank for your assistance. 

actually wanted it to troubleshoot my SD card reader.. duff card.

---


---
title: "Default Programmes for new user"
date: 2007-11-03
forum: General Help
---

### Post by theDaveTheRave on 2007-11-03
Hello All.

I'm reasonably new to linux, but learning all the time.

I've just had a total HDD failure and replaced the Laptop HDD. I've installed everything and it works a treat.

However, I added my GF as a user on the laptop - as I thought I should be able to get this to work and it was good practice etc.

But mainly it was so as when I'm not around she can use this one , rather than the desktop if required, and still access her email / web etc.

Well she tried to watch a DVD the other night but VNC didn't work as it hasn't been installed into her system.

How do I set up a group of "non standard" programes that any new user can use once I add them to the system? (obviously Firefox, evolution, and lots of other stuff work when I add my GF as a user.... what makes them specia? do they live in a specific place?

You help is greatly appreciated, I've searched everywhere for an answer to this so if you can point me in the direction of where I need to go that will be great.

again thanks in advance.

Dave

---

### Post by Pumalite on 2007-11-03
sudo apt-get install ubuntu-restricted-extras
Add Medibuntu to your sources list:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)
And install all needed codecs.
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by Thyme on 2007-11-03
Hi theDaveTheRave  ,

To my knowledge, programs that are installed in "/usr/local" will only be available to the user logged into the system - and if he is the user who installed the program (has ownership of it). 

However, programs that are installed in /usr/share (like firefox, evolution etc ..) will be available to all users, irrespective of who installed the program.

---

### Post by theDaveTheRave on 2007-11-03
Thyme.

Thanks for the advice.

> However, programs that are installed in /usr/share (like firefox, evolution etc ..) will be available to all users, irrespective of who installed the program.

But now I feel really dopey as I realise I should have been able to work that out for myself!

Pumalite, thanks for the help, but VLC functions fine from my user area, but not at all from my GF's - this did quite nark me as I thought I have added it to the system usind <sudo>.... but as I begin to think about it I realise that this can't be the case.

So very quickly, do I need to do anything special other than install all the codecs and stuff in the /usr/share directory.... and if so how do I do this? as I have loaded VLC previously through synaptic (which is great....  but it obviously only puts the stuff into the local user area.

Am I going to have to download the codecs and stuff and install manually?? and if so how am I then going to remove the old one... so as Idon't have 2 copies floating around? and what about updates? will they be automatically placed in the correctly place for VLC once it is in the system??

Appologies as it does seem to have become a more all encompasing issue!

thanks again in advance.

Dave

---


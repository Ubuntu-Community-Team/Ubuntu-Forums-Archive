---
title: "Clickin somethin from system,nothing happens"
date: 2008-05-18
forum: General Help
---

### Post by manosone on 2008-05-18
Alo to everybody.Well here is the problem.When i 'm clicking one of the:software sources,login windows,hardware drivers,synaptic pack. manager.,and others,nothing happens.The circle counts for about 5 secs an then nothing happens.I created another user(dekstop and admin)an tried to do the same.Nothing happened again.Moreover when i'm running synaptic from terminal,it runs.I didnt checked the others cause i do not know the right commands.I am a new user by the way and i am running heron.Any ideas?

---

### Post by forestpixie on 2008-05-18
Run synaptic from a terminal see if you get an error

```
gksudo synaptic
```

---

### Post by manosone on 2008-05-18
> **forestpixie said:**
> Run synaptic from a terminal see if you get an error

```
gksudo synaptic
```
Well gksudo synaptic returns nothing.
What does "gk" stands for?Cause when i run synaptic from terminal,it runs.By the way it showed an error message which was something like this:Some settings could not[...].Gnome will try to restart[..].I tried after that to  run on recovery and use the "repair broken packages" dpkg.Problem not solved.

---

### Post by manosone on 2008-05-18
Alo again all.Well i tried the "try to fix x server".I wasnt sure about what is gonna happen but took the "risc".Nothing happened.As i've told you above some apps wont open.ex Login Window,Software Packages,but others work.ex.System monitor,Power Managment,Service settings.The easy way is to format and install hardy again,but i want to learn how to fix this.Anyone would like try to help me?

---

### Post by forestpixie on 2008-05-19
gksudo is apparently better to run graphical apps with rather than sudo - I did have some problems right at the beginning that I believe were caused by not using it - so now I do, whether that was the case I do not know :)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

You should have got something in the terminal from running the gksudo synaptic command - you did run it from the first account you set up at install time I assume. That account gets sudo oines you add later don't.

Yes - reinstalling would probably be easier and quicker, but I know what you mean about trying to sort problems first. Although that said I did install 3 times in 1 week when I was mucking about with things.

---

### Post by sdennie on 2008-05-19
It sounds like gksudo might be broken.  Can you post the exact errors you get running "gksudo synaptic".  Also, try:

```

sudo apt-get install --reinstall gksu

```

---

### Post by manosone on 2008-05-19
Thanks people.I lik to see people who want to help.Well i wrote sudo apt-get install --reinstall gksu.When i wrote gksudo synaptic and it worked.No errors and synaptic opened.But i still got the problem to run other apps from gui.Does enyone knows how to run from terminal the "hardware drivers" or "login window" or "software sources" in order to check if the work this way(cause with gui they do not)???

---

### Post by forestpixie on 2008-05-19
```
gksudo gdmsetup
gksudo software-properties-gtk
gksudo jockey-gtk
```

---

### Post by manosone on 2008-05-19
First of all,thanks.Well,i think that something is wrong.When i wrote gksudo synaptic nothing happened.No errors.The cursor just goes a line down and it waits,till i hit ctrl+c to stop it.The same happens when i hit the commands forest wrote above.BUT when i hit sudo apt-get install --reinstall gksu and AFTER that hit any of the above commands,they work.Morevoer,i loged out and back in to see what will happen.When i loged back in happened the same as above:When i wrote gksudo synaptic nothing happened.No errors.The cursor just goes a line down and it waits,till i hit ctrl+c to stop it.The same happens when i hit the commands forest wrote above.BUT when i hit sudo apt-get install --reinstall gksu and AFTER that hit any of the above commands,they work.Now,any ideas?

---

### Post by sdennie on 2008-05-19
Are you on a laptop with a fingerprint reader and did you install the drivers for the reader?  It's possible to semi-break gksudo in that case.  Try starting synaptic from System->Administration.  If it doesn't come up, wait a second and try again from System->Administration.

---

### Post by manosone on 2008-05-19
Well yes i am on an acer aspire 5720z(in case that matters) but i got no fingerprint reader.Morevover forest i did not understood that..> **forestpixie said:**
>  you did run it from the first account you set up at install time I assume. .
I am about to re-install hardy but i do  not want to.If that happens again i will like to know how to fix this...

---

### Post by forestpixie on 2008-05-19
> Morevover forest i did not understood that..You said that you setup a new account - I believe that sudo etc will run from the original account setup during installation, but not necessarily from any that are made afterwards.

Although I could be wrong - maybe vor knows?

---

### Post by signseeker on 2008-05-19
forest - you are correct. if a new user account is made that user needs to be added to the admin group in order to be able to use sudo.

---

### Post by sdennie on 2008-05-19
Right.  In order to give a user admin privileges you either have to go to System->Administration->Users and Groups->Unlock then double click on the user and add them to the admin group in the properties tab.  Or, much easier is to just do the following from the command line:

```

sudo addgroup the_username admin

```

---

### Post by manosone on 2008-05-20
Thanks once again.Well now i got it.The new user that i had create was an admin account.Moreover the commands we said above to run,were runned with the only account(except the root) i have.I deleted the second user that i created.Did you mentioned my last post?
> **manosone said:**
> First of all,thanks.Well,i think that something is wrong.When i wrote gksudo synaptic nothing happened.No errors.The cursor just goes a line down and it waits,till i hit ctrl+c to stop it.The same happens when i hit the commands forest wrote above.BUT when i hit sudo apt-get install --reinstall gksu and AFTER that hit any of the above commands,they work.Morevoer,i loged out and back in to see what will happen.When i loged back in happened the same as above:When i wrote gksudo synaptic nothing happened.No errors.The cursor just goes a line down and it waits,till i hit ctrl+c to stop it.The same happens when i hit the commands forest wrote above.BUT when i hit sudo apt-get install --reinstall gksu and AFTER that hit any of the above commands,they work.Now,any ideas?




*(By the way sorry if my english are kinda bad,but i am working on that.:))

---

### Post by manosone on 2008-05-30
Well,finally problem not solved,so i re-installed ubuntu.Anyway,thanks a lot to everyone who helped:).

---


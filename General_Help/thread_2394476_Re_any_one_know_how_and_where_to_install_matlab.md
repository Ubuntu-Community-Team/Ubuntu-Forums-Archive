---
title: "Re: any one know how and where to install matlab?"
date: 2018-06-16
forum: General Help
---

### Post by bodhin2 on 2018-06-16
my wife wanted it on her laptop - tried to install via ubuntu store amd it asked where to install it?  tried something but did not know what i was doing and even before i tried to fill in the blank - it just kept saying nothing there - where do you want it.  tried to quit and there was a warning about not completing install.  but no way to quit other than just hit the quit despite the app laoding warning.  thing is it wasn't loading.  sorry things are so vague.  i was just trying to help her out.  i do not need it.  this was the only weird exception to installing stuff for me via the store.  thanks.

ok i found some info and it also calles for one to have the commercial package - found it out the hard way.  in the store it says it is still installing but no way to cancel or delete - any commands to remove whatever i did install or is trying to install please?

the incomplete install appears to have messed up certain other stuff in the apps store.  man - tried to help my wife out and all the work went down the tubes.  i should have left it all as it was.  thanks for any help.

---

### Post by Frogs Hair on 2018-06-16
Did you install the package used to configure an existing installation of MATLAB?

---

### Post by bodhin2 on 2018-06-16
hey thanks for the speedy reply  i was trying to install the matlab in the ubuntu sofatware store area.  we found out later it is not the app but an installer i guess to set it up now it is frozen in the store.  and no way to cancel it or delete it.  i tried and searched all over.  Thanks FH.  sorry for the panic attack here.  just ticked i messed up a nice working system trying to help her out. she's a physicist.....

---

### Post by Frogs Hair on 2018-06-16
Log out and back in and we can do some clean up from the terminal.

---

### Post by bodhin2 on 2018-06-16
ok doing now, did not see any logout so shutdown and powering up - i did try a reboot before to by the way.  man i will never try anything stupid like this again.  heh heh !

found logout.

---

### Post by Frogs Hair on 2018-06-16
If it's totally frozen you might have to hold down the power button till it shuts down.

---

### Post by bodhin2 on 2018-06-16
no shutdown but is says password regquired by an application not wanting to shut down.  the matlab in the store is so-called frozen trying to install - and no cancel is possible.

clarification - this is the matlab installer or whatever it is called in the ubbuntu store.  not the actual matlab app we thought that is what we were installing and turns out it isn't. really dumb.

---

### Post by Frogs Hair on 2018-06-16
Did you enter a password when you began the installation ?

---

### Post by bodhin2 on 2018-06-16
i am sorry to say i do not remember....  my bad...

everytime ypu power off the app requiresyou to do a password

---

### Post by Frogs Hair on 2018-06-16
> **bodhin2 said:**
> clarification - this is the matlab installer or whatever it is called in the ubbuntu store.  not the actual matlab app we thought that is what we were installing and turns out it isn't. really dumb.

See post #4

---

### Post by bodhin2 on 2018-06-16
yes that is it....

---

### Post by Frogs Hair on 2018-06-16
Minimize the software store window and check for a password window if possible. 

Edit: Do you have terminal access? If so try the following . ```
killall gnome-software
```

---

### Post by bodhin2 on 2018-06-16
ok nothing.  also when i looked at the install there was no! warning in yellow and when i searched for matlab - it seemed like it was possible to install.  so even though i rebooted and shutdown, maybe the logout cleared something or the shutdown did.  reboot did not do anything.  more likely the logout did it.

thank you my friend - i owe you somehow!!!!!!

anyone runs into this scenario - completely shutdown, login and logout and then logback in.  something in there worked!!  Thanks Frogs Hair.  save my butt again.

i usually go by - if it's not broke then don't fix it; and if you can't fix it then don't break it.

seems like no need for the kill all command.  Ok???  :-)

my wife said thank you too!

---

### Post by Frogs Hair on 2018-06-16
Were not done! :o 

Run the following command and report any errors . ```
sudo apt update
```

---

### Post by bodhin2 on 2018-06-16
ok did it
said all packages up to date after running a bunch of stuff

```
pei@pei:~$ sudo apt update
[sudo] password for pei: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [83.2 kB]   
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]    
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB] 
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [105 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 48x48 Icons [18.0 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 64x64 Icons [34.2 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [120 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 48x48 Icons [121 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [195 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [5,100 B]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [2,452 B]
Fetched 841 kB in 2s (410 kB/s)               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
pei@pei:~$
```

in case you needed this.  if not delete or i can

---

### Post by Frogs Hair on 2018-06-16
Looks like it should , your'e out of woods. If you had a partially installed package it would have showed up in the output with instructions to resolve any problem.

---

### Post by bodhin2 on 2018-06-16
ah Ok ---- i see now why you asked me to run it.

Thank you again.

anything else or we are done?

---

### Post by Frogs Hair on 2018-06-16
> **bodhin2 said:**
> anything else or we are done?

Were done , you may have search for a tutorial to install Matlab on _18.04_ . Just take your time an remember there are people here with experience installing it though I'm not one of them.

---

### Post by bodhin2 on 2018-06-16
yes i found it and that is where we caught or confusion...  also looking into synaptic too

---


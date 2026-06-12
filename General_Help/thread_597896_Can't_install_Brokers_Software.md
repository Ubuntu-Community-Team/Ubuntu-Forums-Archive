---
title: "Can't install Brokers Software"
date: 2007-10-30
forum: General Help
---

### Post by earlgray on 2007-10-30
I'm unable to install my brokers software. It's a DOS/Windows executable file.
When I try and open it I get an error message. It says there are no applications available to run the software (or something like that).
The software is from Rush Group. Its called Direct Pro for Terra Nova

---

### Post by akiratheoni on 2007-10-30
Are you using Wine? If not, install it with:

```
sudo apt-get install wine
```

Then right click on the executable, select 'Open with other application', then a window will pop up asking you what program to open it up with. Then click the arrow that says 'Custom Command'. A text input area will appear, type:

```
wine
``` 

into it. Hit OK. Then double click on the file and it should open with Wine. If it doesn't, you'll need to navigate to the directory through the terminal, then use this command:

```
wine nameofprogram.exe
```

Then you'll be greeted with an output, then post it here.

---

### Post by Maestro23 on 2007-10-30
WineHQ: [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by earlgray on 2007-10-30
Thanks for your info on Wine. Today before i joined this form I tired downloading Wine  but I ended up with 2 files I didn't know what to do with.
I just installed Ubuntu yesterday and I really don't know how to do most of the basic procedures.
Please let me know where I go to type in the code you mentioned in the beginning of your reply
"sudo apt - get install wine"
Thanks

---

### Post by Spenzer4Hire on 2007-10-30
To install WINE you must type 'sudo apt-get install wine' into a terminal (think Windows command prompt).

The terminal can be opened from Applications > Accessories > Terminal

Make sure to type the command exactly as I have (previously you added spaces).

---

### Post by earlgray on 2007-10-31
Thanks for the reply
I tried installing wine but get the following response:
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libaudio2 but it is not installable
E: Broken packages
dave@UbuntuDell:~$ 

eg

---


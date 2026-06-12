---
title: "Re: Password is not accepted in the graphical user interface - no authori"
date: 2021-03-21
forum: General Help
---

### Post by ingolf3 on 2021-03-21
Hello,
I'm very new here and don't have much of a clue yet.

On an older laptop with an Ubuntu minimal installation + Lubuntu, the password is only accepted in the terminal.
In the graphical user interface of the programs 'Plausma-Discover' & 'Software-Center' the error message "You do not have authorisation to perform this operation" or "You do not have sufficient user rights to install applications" appears after entering the password.
Then comes the error message: "PolicyKit Handler terminated unexpectedly".
The user is the 1st one created during installation, belongs to the sudo group.
From the terminal it is possible to update and install.
All programmes are up to date.

Does anyone have any ideas?
Greetings

Thank you for answers.

.... not so much idea yet

---

### Post by guiverc on 2021-03-21
> **ingolf3 said:**
> 
On an older laptop with an Ubuntu minimal installation + Lubuntu, the password is only accepted in the terminal.

In the graphical user interface of the programs 'Plausma-Discover' & 'Software-Center' the error message "You do not have authorisation to perform this operation" or "You do not have sufficient user rights to install applications" appears after entering the password.


How did you install Lubuntu?   

I wonder if you only installed part of it? or did you install `lubuntu-desktop` to your minimal Ubuntu system?

Are you using `sddm`as the display manager & greeter?
Are you using a qwerty keyboard? and what is your configured language?

The Lubuntu manual page for installing software can be seen at [https://manual.lubuntu.me/stable/4/Installing_Updating_and_Removing_Software.html](https://manual.lubuntu.me/stable/4/Installing_Updating_and_Removing_Software.html)

It lists two primary options for installing software

[LIST]
[*][Discover Software Center]("https://manual.lubuntu.me/stable/4/4.1/discover.html")
[*][Muon Package Manager]("https://manual.lubuntu.me/stable/4/4.2/muon.html")
[/LIST]

By "Plausma-Discover" and "Software-Centre" do you mean the "Discover Software Center" which was created by the Plasma Development Team (for KDE Plasma). 

Are you asked to enter your password? 

> **ingolf3 said:**
> 
Then comes the error message: "PolicyKit Handler terminated unexpectedly".


At this message, I'd have a look in /var/crash/ which is the directory where crash dumps are placed when something goes wrong. The name of .crash files is a huge clue as to where problems occurred; the date & timestamp of the file tell you when (which would be seconds-minutes before when I usually look).

If there was nothing added to /var/crash; I'd likely look in system logs (`dmesg` and `journalctl`; both at the end or most-recent, assuming you're looking straight after you got the error).  I'd also probably try again after looking, to see if the same message occurs again (or if you didn't recognize it, it should not be easier to spot as I'd expect messages to now be there twice with timestamps varying by the seconds/minutes between tries).

Do you have a .crash file? and if you look in system logs do you see  anything?

Note: I'm not a big Discover user, it's nice & pretty, but I prefer terminal commands, or if i want to select packages to install I prefer `aptitude`, and if I had to use the two offered in the Lubuntu manual, I'd likely use `muon`.

---

### Post by ingolf3 on 2021-03-21
Oh, hello, sorry to see it so late.

One moment please

Thank you very much for your very detailed message.

I have to translate it first and then understand it ;-)

[https://www.deepl.com/translator](https://www.deepl.com/translator)

> **guiverc said:**
> How did you install Lubuntu?   

I wonder if you only installed part of it? or did you install `lubuntu-desktop` to your minimal Ubuntu system?

I installed Lubuntu by doing a minimal Ubuntu installation from a live CD and then Lubuntu 20.04 from the Lubuntu site. 


Are you using `sddm`as the display manager & greeter?

Not sure. How can I find out?
What is `sddm`?


Are you using a qwerty keyboard? and what is your configured language?

Yes, german.


The Lubuntu manual page for installing software can be seen at [URL="https://manual.lubuntu.me/stable/4/Installing_Updating_and_Removing_Software.html"]https://manual.lubuntu.me/stable/4/Installing_Updating_and_Removing_Software.html


Thank you
[/URL]
By "Plausma-Discover" and "Software-Centre" do you mean the "Discover Software Center" which was created by the Plasma Development Team (for KDE Plasma). 

Yes

Are you asked to enter your password? 

Yes, in "Plausma-Discover" and "Software-Centre" this is the problem, it is not accepted there. 

Immediately further  ;-)

[QUOTE=guiverc;14027552]
At this message, I'd have a look in /var/crash/ which is the directory where crash dumps are placed when something goes wrong. The name of .crash files is a huge clue as to where problems occurred; the date & timestamp of the file tell you when (which would be seconds-minutes before when I usually look).

If there was nothing added to /var/crash; I'd likely look in system logs (`dmesg` and `journalctl`; both at the end or most-recent, assuming you're looking straight after you got the error).  I'd also probably try again after looking, to see if the same message occurs again (or if you didn't recognize it, it should not be easier to spot as I'd expect messages to now be there twice with timestamps varying by the seconds/minutes between tries).

Do you have a .crash file? and if you look in system logs do you see  anything?


Thank you very much, I'll do it right away!



Note: I'm not a big Discover user, it's nice & pretty, but I prefer terminal commands, or if i want to select packages to install I prefer `aptitude`, and if I had to use the two offered in the Lubuntu manual, I'd likely use `muon`.


Thank you very much for your efforts.

Get me back in touch.

Thank you.

---

### Post by cmcanulty on 2021-03-21
It is a "feature" of the newer ubuntu releases to stop that function but there is a fix that is very easy
   For root access to graphical applications:  

  1)temporary fix without logging out:
 
```
  xhost  +SI:localuser:root
```

  2) permanent fix

  edit or create file in/home/yourusernamehere 

  name it ./xinitrc and put in text below

```
   xhost   +localhost  &

```

---


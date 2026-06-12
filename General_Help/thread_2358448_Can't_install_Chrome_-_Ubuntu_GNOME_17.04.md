---
title: "Can't install Chrome - Ubuntu GNOME 17.04"
date: 2017-04-13
forum: General Help
---

### Post by mckempt2 on 2017-04-13
Hello,
I installed Chrome from Google's website (made sure to 'Save') but when it opens the software manager I can't get past pressing the button and literally nothing happening. Just a completely dead button.

I tried doing regular 'sudo apt-get install google-chrome-stable' and it's apparently not there.

Any help?

---

### Post by deadflowr on 2017-04-13
Use apt like
```
sudo apt install ~/Downloads/google-chrome-stable-version-number-here.deb
```
quick tip when you enter the google-chrome press tab to let it auto complete the full name.
so just type google-chrome-TAB button and it should autofill the rest, including the .deb, if that makes sense.


EDIT: you seem to have marked this as solved, was it?

---

### Post by russkyca on 2017-04-15
> **deadflowr said:**
> Use apt like
```
sudo apt install ~/Downloads/google-chrome-stable-version-number-here.deb
```
quick tip when you enter the google-chrome press tab to let it auto complete the full name.
so just type google-chrome-TAB button and it should autofill the rest, including the .deb, if that makes sense.


EDIT: you seem to have marked this as solved, was it?I don't see how it is as I couldn't install Chrome either.    (Note:  I eventually did using another method - explained below).   

I chose, initially, to install it straight from the Google Chrome website.   I selected 'Download' and the Debian/Ubuntu .deb and then the default Ubuntu Software application - as it should add the repository, right?   But, when the Software program opens up, you have the 'Install' button and after clicking it, nothing happens.   Nothing.   No message or window pops up including no window for authorization.   Zilch.  

I tried it a couple times thinking maybe I did something wrong or missed a step.   But, the same thing happened.

There are old instructions for using CLI that various people have uploaded to websites (they don't mention 17.04 but they do mention 16.04 and 16.10 so I thought maybe 17.04 still applies) and did it that way.   Using the command line, they suggest adding the key (wget), setting the repo and then update/installing.   Can I say this?    It worked for me.   I don't think the problem is 'solved' though.   There should be some sort of message after you try to click 'install' using the download method directly from google.   I don't know what this means so I hope others try the first method and see what they get.   It will be interesting if it will be repeated on other systems or if it's just mine (not sure if the OP was explaining the same experience but kinda sounded like it).

I just installed Ubuntu Gnome 17.04 this morning and have installed other software programs so this shows that I can install programs/software using the GUI method with the default application (i.e. Ubuntu Software program) .

---

### Post by lamnite on 2017-04-17
Hey! I'm sorry to bother you. I've encountered the same problem as you, but I'm a bit of a noob. Can you tell me, step by step, how you installed Chrome through the terminal? Thanks!

edit: I managed to install chrome.

---

### Post by tatsujb on 2017-04-17
> **russkyca said:**
>   they suggest adding the key (wget), setting the repo and then update/installing.

this is chinese to any beginner reading this thread.

please paste your command line history that concerns this issue and your solution.

---

### Post by coffeecat on 2017-04-17
What's the easiest (newbie friendly) way of installing Chrome browser since software manager still appears to be unreliable in use?  That is, in my opinion. And this works in 17.04. I've just done it - three times. 

1 - download the deb package from [https://www.google.co.uk/chrome/browser/desktop/](https://www.google.co.uk/chrome/browser/desktop/) 

2 - Install the gdebi package from the Ubuntu repositories, using whatever your favourite GUI package manager is, or apt from the command line.

3 - Right-click on the downloaded google-chrome-stable*.deb package, and choose "open with..." gdebi. Type your password in when prompted.

4 - Bob's your uncle.

---

### Post by Joscha on 2017-04-17
> **coffeecat said:**
> What's the easiest (newbie friendly) way of installing Chrome browser since software manager still appears to be unreliable in use?  That is, in my opinion. And this works in 17.04. I've just done it - three times. 

1 - download the deb package from [https://www.google.co.uk/chrome/browser/desktop/](https://www.google.co.uk/chrome/browser/desktop/) 

2 - Install the gdebi package from the Ubuntu repositories, using whatever your favourite GUI package manager is, or apt from the command line.

3 - Right-click on the downloaded google-chrome-stable*.deb package, and choose "open with..." gdebi. Type your password in when prompted.

4 - Bob's your uncle.



For all those dumb users like myself:

 sudo apt-get install gdebi  

 ought to install GDebi. Once you've got that, it's a piece of cake following coffeecat's advice. ;-)

---


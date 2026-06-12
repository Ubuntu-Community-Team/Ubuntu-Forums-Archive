---
title: "Installed programs disappear from search and unavailable from terminal"
date: 2014-11-26
forum: General Help
---

### Post by Fsirett on 2014-11-26
I cannot find anything similar when I search, so I am assuming this is not very imprtant or difficult to fix.

This all began when I installed and started using Chrome for some things. I still use Firefox as my main browser, but I decided to try Chrome. I do have Chromium installed as well, but that is just because I am too lazy to remove it. 

All went fine until yesterday or the day before when Chrome disappeared. I did not see it on the tool bar and it did not appear on the search page either. I reinstalled Chrome and still no joy. Then this afternoon, when I tried to acces Clamantine, I found it had gone the same way, as had Rhythmbox, Audio still plays just fine, but it does not let me access either of the two audio programmes I have occasion to use. I am assuming this is something common and not very complex, at least I certainly hope it is!

There are no error messages and things at home on the toolbar seem to work fine. However...


Cheers

Frank Sirett

---

### Post by carlwsnyder on 2014-11-26
When was your last system update from Ubuntu's repositories?  I have sometimes had these type of problems with programs disappearing from menu or program lists if they are not updated because they are not properly registered as coming from the repositories, but not for any other reason.
```
dpkg -l
```(that is a lower case L) will list the programs you have loaded on your system available from the terminal.  Are you installing using **apt-get **or **aptitude** from a terminal window, **Synaptic** or the Ubuntu Software Center from your desktop, or are you getting installation files from source code or random spots on the Internet?  Google Chrome, at least, I know installs from Google's repositories, but the .deb file from Google updates your sources list to include the Google repositories for your distribution.

---

### Post by Fsirett on 2014-11-26
Cheers for that! I just ran the code and it changed nothing, I am afraid. Looked for both Chrome and Clementine and both are not listed. 

However, I did go to the settings default applications and I see both programmes are still listed. This is very odd indeed!

---

### Post by ajgreeny on 2014-11-26
What exactly do you mean by
> I did not see it on the tool bar and it did not appear on the search  page either. I reinstalled Chrome and still no joy. Then this afternoon,  when I tried to acces Clamantine, I found it had gone the same way, as  had Rhythmbox, Audio still plays just fine, but it does not let me  access either of the two audio programmes I have occasion to use.
and what DE are you using; unity (the default) or something else?

---

### Post by Fsirett on 2014-11-27
Hmmm. I thought I posted a reply to this yesterday but it seems to have not taken. Sorry for the delay.

First of all, I am using the defalt Unity and Ubuntu 14.10

Next, I had both Clementine and Chrome on the toolbar on the left and they both disappeared, but that might have been nothing more than my not having locked them there.

When I use the search button and ask for either programme I get no hits at all. Very odd.

When I go to settings and look at the default programmes both are still on the lists as options.

When I updated the code (dpkg -l) the readout included both Chrome and Clementine.

I hasten to add these are just the programmes I have found thus far that are not responding. There may easily be many more, that I have not asked for yet

Cheers

Frank Sirett.

---

### Post by ajgreeny on 2014-11-27
I don't use either of those applications so don't know what the executables are called, but search in /usr/bin for clementine, if it there run command in terminal **/usr/bin/clementine**, and if it starts, make sure you lock it to the launchbar (the correct name for the toolbar on the left).

You can do similarly for Chrome, though I have a suspicion that google-chrome maybe installed to /opt (not sure about that, so search both /usr/bin and /opt), and once started make sure to lock it to the launchbar.

---

### Post by flaymond on 2014-11-27
Executables in Ubuntu is called ***.deb ***because Ubuntu is based Debian. Some of the programs can be fetched using Launchpad.

---

### Post by vasa1 on 2014-11-27
> **ajgreeny said:**
> I don't use either of those applications so don't know what the executables are called, but search in /usr/bin for clementine, if it there run command in terminal **/usr/bin/clementine**, and if it starts, make sure you lock it to the launchbar (the correct name for the toolbar on the left).

You can do similarly for Chrome, though I have a suspicion that google-chrome maybe installed to /opt (not sure about that, so search both /usr/bin and /opt), and once started make sure to lock it to the launchbar.Or OP can run```
which google-chrome
```and that gives me```
/usr/bin/google-chrome
```on Lubuntu 14.04.

---

### Post by Fsirett on 2014-11-27
Cheers fopr your help, all of you. 

I used the which command (another for my growing list) and found Clementine was in the usr/bin file, went there and opened it from there. No problem on that score so I went and looked at opening a bunch more programmes that I rarely use and they all opened without a hitch ( from the usr/bin file)

I went on and looked for chrome and found that listed in the usr/bin file but only things that wopened with an editor. Taking your advice I went to the opt file and found nother bunch of chrome files, some of which were run files. They say "run," but not for me. Thinking about it, I shall root around in other places to see if there is something there and if not I will remove Chrome and reinstall it. It was running and seemed to be happy, but now it has decided it will not run.

As I say, many thanks for what you have told me. Chrome is not quite as important to me as Clementine - So much better than Rhythmbox for me - but Chrome is just an extra bit that I want to experiment with. As long as this is either isolated or unimportant to the system, I am relieved.

I shall leave this thread open in case there is more ideas and I want to post my results for those who come this way. Even the stupid have their uses sometimes.

Frank Sirett

---

### Post by Fsirett on 2014-11-27
I have just looked through all of the hidden files and actually restrained myself from pshing unknown buttons or changing things. That takes some discipline for me.

In any case there were no other instances of either google or google-chrome. I decided to rid myself of the problem and start again. 

For my new enterprise I referred to: [http://028499.com/how-to-install-google-chrome-on-ubuntu-14-10-or-linux-mint-18-or-ubuntu-14-10-mate-edition/](http://028499.com/how-to-install-google-chrome-on-ubuntu-14-10-or-linux-mint-18-or-ubuntu-14-10-mate-edition/)

and I used their last section to remove the instance of the programme that I have on. To my surprise, I get back the message "cannot remove ‘google-chrome’: No such file or directory" 

I have tried shortening the command and even changing the names to the files that I see, but all to no avail. For some reason the computer has decided not to see what I can see clearly in the usr/bin file and the opt file. I would really rather not go in and simply delete the file, there be dragons... I know, I have seen more than enough of them that have ambushed me. 

In any case, we now know that the programme itself has a fault that hides it from the system so the next question is: How do I delete the thing when "rm" does not seem to do the trick?

Cheers again

Frank Sirett

---

### Post by CantankRus on 2014-11-27
> **Fsirett said:**
> I have just looked through all of the hidden files and actually restrained myself from pshing unknown buttons or changing things. That takes some discipline for me.

In any case there were no other instances of either google or google-chrome. I decided to rid myself of the problem and start again. 

For my new enterprise I referred to: [http://028499.com/how-to-install-google-chrome-on-ubuntu-14-10-or-linux-mint-18-or-ubuntu-14-10-mate-edition/](http://028499.com/how-to-install-google-chrome-on-ubuntu-14-10-or-linux-mint-18-or-ubuntu-14-10-mate-edition/)

and I used their last section to remove the instance of the programme that I have on. To my surprise, I get back the message "cannot remove &#8216;google-chrome&#8217;: No such file or directory" 

I have tried shortening the command and even changing the names to the files that I see, but all to no avail. For some reason the computer has decided not to see what I can see clearly in the usr/bin file and the opt file. I would really rather not go in and simply delete the file, there be dragons... I know, I have seen more than enough of them that have ambushed me. 

In any case, we now know that the programme itself has a fault that hides it from the system so the next question is: How do I delete the thing when "rm" does not seem to do the trick?

Cheers again

Frank Sirett
The rm command in that post is simply to delete the downloaded .deb file after you have installed it.
The command does not use a path to the deb file so you need to be in the directory where the deb is for it to work or 
much simpler just delete it through the file browser.
I would say more likely than not your current problems have been caused by you running commands you don't fully understand due to this comment...
> and actually restrained myself from pshing unknown buttons or changing things. That takes some discipline for me.

---

### Post by Fsirett on 2014-11-27
Entirely possible, but I did get the advice from a web site that told me to use it to uninstall. It did not work, and that is the long and short of it.

As for pushing buttons, it is now something of a joke. When I first began using Ubuntu, i was fascinated by how it all worked and I would try to change things to see what would happen and understand what was going on. I spent a lot of time reinstalling , but I did learn quite a bit.

I am not likely to use many commands without some guidance Now I know, I shall move to the folder and delete the file and start again. However, when you say go through the file browser, do you mean just open the file and delete the folder? I thought that would be a bad idea, hence I try not to do that. However, if you are telling me it is the way to go, I shall do so!

I await your confirmation

Cheers

Frank Sirett

---

### Post by ajgreeny on 2014-11-27
It could be worth installing synaptic package manager, as I think it is without doubt the best way to install, and also to uninstall applications that you have installed using the normal package management systems of Ubuntu.

It is what I tend to use for every such activity that I carry out, and is a lot more informative and flexible than any other means of installing/uninstalling available to us apart from the terminal.  It used to be part of the default installation but now has been overtaken by software-centre which in my opinion is not nearly as good.

---

### Post by lisati on 2014-11-27
> **InterProg said:**
> Executables in Ubuntu is called ***.deb ***because Ubuntu is based Debian. Some of the programs can be fetched using Launchpad.

Not quite. A .deb file is a *package* used for installation.

---

### Post by Fsirett on 2014-11-28
I seem to remember the Synaptic Package Manager, but I have never been fully conversant with its use. All of my advice to installing Chrome has been using command line, but with that very timely tip I shall look up all of the information on using it I can. It does seem like a very useful tip.

Cheers fro all your help!

I am going to just go and delete the offending programme now. From what I understand, my reluctance is due to a Windows hangover whereby removing a programme like that cold often completely break your system; a horror with Windows, but an inconvenience with Ubuntu. A few hours as opposed to an entire day...if I am lucky!

I am then going to install the Synaptic Package manager and look for the appropriate software from Google and use that. 

Cheers all

Frank Sirett

---

### Post by Fsirett on 2014-11-28
I have just been playing with the search featurea and the filter options, thinking I could no no more harm. One of the things I uncovered was the option to enable a search that included "applications." I enabled it and almost everything else decided to come back. All that I knew were a problem, but there may beother things. 

Ubtil the next time, thank you all for your help,and  patience, especially with my bad typing and typos

Cheers again

Frank Sirett

---


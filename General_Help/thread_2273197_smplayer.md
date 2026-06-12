---
title: "smplayer"
date: 2015-04-11
forum: General Help
---

### Post by george110 on 2015-04-11
I'm trying to install smplayer & downloaded as a start

[B][smplayer-14.9.0.6690.tar.bz2]("http://downloads.sourceforge.net/smplayer/smplayer-14.9.0.6690.tar.bz2")

together with a set of instructions [/B]:
sudo add-apt-repository ppa:rvm/smplayer
  sudo apt-get update
  sudo apt-get install smplayer smplayer-themes smplayer-skins 

 & to run these commands in a terminal.   

Now following instructions after smplayer was downloaded & opening saw an extraction which grew the file from about 2mbs to 28 mbs & on opening the enlarged file were displayed many other files but no smplayer opewning file.

What actually do I need to do to have smplayer on my computer & where is the terminal within which to put these commands - & when do you put in the commands ? Does anybody know & if so is anyone prepared to help ?

---

### Post by nerdtron on 2015-04-11
HHmmm what's wrong with the smplayer from the Software Center? Just click install and no more hassle.

---

### Post by Holger_Gehrke on 2015-04-11
The file you downloaded was probably the source code. To generate an executable from that, you'd need a compiler and some other tools and of course the right libraries in developers versions (including header files). So unless you want to go down that road, you can just delete that tarball and the files you extracted from it.

An introduction to the terminal and it's use can be found in the [community wiki]("https://help.ubuntu.com/community/UsingTheTerminal?action=show").

---

### Post by george110 on 2015-04-11
There are no " install" options just " open " after the file is downloaded and here the choice of options is " extract ". I'm running a 14.10 .

---

### Post by george110 on 2015-04-11
Thank you for replying. The instructions from the download page said to go to the terminal & type the instructions provided & what was downloaded will open - a shorter journey. Where is the terminal ? If you know then perhaps you could  answer just one more time that question.

---

### Post by coffeecat on 2015-04-11
Please re-read nerdtron's post at #2. Was there a particular reason you wanted to do this the difficult way?

---

### Post by george110 on 2015-04-11
How do I navigate to your #2 ? There are no options available from your post which direct me to your #2.

---

### Post by nerdtron on 2015-04-11
> **george110 said:**
> There are no " install" options just " open " after the file is downloaded and here the choice of options is " extract ". I'm running a 14.10 .

If you need an "install" option. Here's the recommended instructions:
Open the Ubuntu Software Center (wait for it to load and update software list, may take a minute or two).
Search "smplayer"
On the results, click SMPlayer, then click install
You will be then asked for your password
Wait for it to download and install.
Finished installing SMPlayer and it should show up on your Application lists.

---

### Post by coffeecat on 2015-04-11
> **george110 said:**
> How do I navigate to your #2 ? There are no options available from your post which direct me to your #2.

Post #2 in this thread. But nerdtron has now posted again with comprehensive installation instructions for smplayer.

A general piece of advice if you want to install any piece of software, is that it is best to check in the Software Centre first. Searching for software and downloading packages is a Windows habit and is best avoided. If you can't find what you want in the Software Centre, start a new thread here and people will be able to help you.

---

### Post by Rob Sayer on 2015-04-11
For lord's sake, please just do what nerdtron suggests and install it from Software Center.  

One of the first things I'd tell linux newbies is to always install software from the repos unless you *really* need to do otherwise.  The software there is beta tested for your mint release.  Installing from 3rd party sources like wherever you got that tar file from is a good way to make your OS more unreliable.  Linux is reliable but you can make it less so.

The bleeding edge version may have some new feature(s) but you'll rarely need them.  They'll also not usually be worth the reliability problems they can cause.

Or it may include the latest bug fixes.  It will almost always contain the newest bugs, and there will be more of those than fixes.

These sort of things can be dealt with but it's not beginner level stuff, and I don't think most more techie users will use 3rd party sources any more than they really need to.

This isn't windows, where it's considered normal to download installer files from god knows where that may do god knows what.  One of the big advantages of linux is installing software from tested independent repositories.  You are actually installing the app exactly the same way the head developer for it installed it on his computer.  Why still do it the windows way?

Try to learn how to use Synaptic Package Manager ... it has a bit more learning curve but I always use that or the terminal to install stuff.  Haven't actually used software manager myself for some time.

---

### Post by george110 on 2015-04-11
I've done as you said but when I click on smplayer, again there's no install option. in fact there's no option at all.

---

### Post by george110 on 2015-04-11
Thank you

---

### Post by george110 on 2015-04-11
smplayer isn't one of the sofware packages at the software centre already existant. How can you obtain it without downloading it from somewere. I take note of your cautions about downloads. This is terribly refined & I'm agast at the level of sophistication. It's a real wake up call & very quickly at that. Thank you. In a matter of seconds you've taken me from nowhere to higher levels of consciousness.

---

### Post by george110 on 2015-04-11
Following your instructions I'll do the best that I can as quickly as possible.

---

### Post by coffeecat on 2015-04-11
> **george110 said:**
> smplayer isn't one of the sofware packages at the software centre already existant. 

Yes, it is. This is what I see in Ubuntu 14.10 Software Centre:

[img]http://ubuntuforums.org/attachment.php?attachmentid=261221&d=1428756331[/img]

Which version of Ubuntu are you using - 12.04, 14.04 or 14.10? And are you using an Ubuntu flavour such as Xubuntu or Lubuntu?

[ATTACH=CONFIG]261221[/ATTACH]

---

### Post by george110 on 2015-04-11
I've finally succeded in installing smplayer. It went well. The only problem I have is to find it on the computer so that I can open it. As of this moment I can't locate it but it's also getting late & I'm a bit tired after a hard days physical work so I'll be fresher in the morning.Thank you for your help.

---

### Post by george110 on 2015-04-11
I must be blind. Anyway I downloaded ( or just installed it as you suggest , I don't know which ) it through the software centre. It took quite a long time with a long orange line extending to the right as one is accustomed to see with windows downloads which is why I think it to have been a download from the internet. As the internet connection doesn't display it's activity I can't actually say where the source of the install actually came from. You could be right & I'd like to feel that you are but as you see I have no way of knowing for certain at this stage but within an act of faith I'll agree with you. Thank you for your concern. Here's an interesting problem. Although smplayer is installed I can't actually find it to open it. Any ideas ? It's a 14.10 version.

---

### Post by nerdtron on 2015-04-11
Can you post your screenshot of the software center that smplayer is installed?

You can click the Ubuntu button on the top-left side to open the search dash. Then type smplayer. Or are there no results showing?

---

### Post by CantankRus on 2015-04-11
As you are having a problem grasping how to use ubuntu and installing software, I suggest 
you also use the dash search as shown by nerdtron, to type in "help" and have a read of the ubuntu desktop guide.
There is also an explanation of software and repositories here....[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by george110 on 2015-04-11
You're very generous with your time nerdtron & I don't want to disappoint you. Feeling more alert this morning I managed to locate & open smplayer & it plays a download that I got from the TV - in this case a music compilation of asorted videos that can run for hours. This program I downloaded is called " Rage " an all night music show. It seems as good as you may expect but there is no accompaning sound. In fact on the top right hand of the desktop screen there is a cross next to the speaker. I'll try to tackle this problem & I don't think you ought concern yourself with this.  I think I should be able to tackle this problem if given some time.

---

### Post by george110 on 2015-04-11
Thank you for your advice & I think that if given some time I ought be able to move along those lines.

---

### Post by coffeecat on 2015-04-11
> **george110 said:**
> In fact on the top right hand of the desktop screen there is a cross next to the speaker.

Your sound is muted. Click on the speaker icon and untick the "mute" line.

---

### Post by george110 on 2015-04-11
Thank you for your interest. I've managed to fix the problem along the lines you suggested.

---


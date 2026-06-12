---
title: "Installing Ubuntu using Wubi"
date: 2007-10-01
forum: General Help
---

### Post by Rana1974 on 2007-10-01
Hi,
I am completely new to the linux system and as such have absolutely no programming background , sad but true, I would like to learn though and so managed to install Ubuntu Fiesty suing Wubi (downloaded from wubi.org). As far as I could understand it seems to me that the linux is not loaded on a partitioned drive but as a virtual machine. I could understant that ...but I have a couple of questions,
1. I can see my windows hard drive and my documens etc. Since this is a virtual machine set up can I copy paste files form my document into a folder on the ubuntu desktop? By the same logic can linux viruses afect the wondows and vice versa?
2. My wireless card is not working I was also thinking of using the ndlswrapper to try to get it to work but it says I have to remove the driver and replace with a new one..so wher eis this replacement going to happen and what if this modification screws up my windows machine and I can't use the wireless there?
3. Is there a place where I can get a look at the over all set up of the linux operating system adn ubuntu...for example as a simple power point slide showing the tiered structure or similar...I am not able to understand where the files such as drivers etc are in the wubi-ubuntu system...guess to used to being spoon fed by microsoft...if i use a terminal and want to look up the software locations etc what should I use as comand...and is there a quick cheat sheet for all the comands that a novice would understand...
Thanks a ton..

The above was the original post placed on ubuntu forum...was referred to the wubi forum..thanks...
I have looked at the nautilus details and now now where the files are being stored...[http://www.cutlersoftware.com/ubuntuinstall/...good](http://www.cutlersoftware.com/ubuntuinstall/...good) site for beginners....but the question still remains..how can I import my windows documents and files etc into the ubuntu desktop/folder...also there is a folder in home home/host/drivers...is this a path to the windows folder for drivers or is it a copy of the drivers folder in the Wubi folder?
I must admit Wubi is great adn Ubuntu is impressive...nice!!!
Thanks for all the help..
Rana

---

### Post by gsiliceo on 2007-10-01
1. You can read files from your windows partition but can't write, is not safe yet. No windows virus wont affect linux, and there wont be linux virus.
2. Can't help you with the ndlwrapper but im sure that it wont affect the wireless in windows.
3. 
For the file structure go [here]("http://geek2live.blogspot.com/2007/09/linux-file-structure.html")
For a guide that answers most common questions newbies have about ubuntu go [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

---

### Post by nooby on 2007-10-02
I copy the older text Rana had
> I can see my windows hard drive and my documens etc. Since this is a virtual machine set up can I copy paste files form my document into a folder on the ubuntu desktop? By the same logic can linux viruses afect the wondows and vice versa?


I read Rana to ask this: My take on her Q. 

Using WUBI Ubuntu Linux which allows me to read and write to the NTFS in windows section. WUBI driwing Ubuntu using a virtual drive.

That would allow virus maker to reach my now unprotected windows parts on the hard drive through Linux. They simply send a Trojan in through the Linux. 

No Linux virus. A Windows virus distributed through the usual ports needed for surfing. A Youtube or a Picture or an innocent looking link to a Congratulation Card? These guys are bad so they try to lure us on thousands of innocent looking pages. Kasperski told the bad guys have more programmers than he had to counter their attacks. So it is a real problem. 

How does one as a user of WUBI Ubuntu protect Windows from being infected through Linux?

---

### Post by ago on 2007-10-02
> **nooby said:**
> How does one as a user of WUBI Ubuntu protect Windows from being infected through Linux?

There are no known linux virus. That means for instance that you can get an infected email, but the virus code will not be executed on Linux. So on Linux the virus will have no effect, BUT the email will NOT be cleaned (unless you install an antivirus), and you can pass the virus by forwarding the email to your friend or saving the attachment to a windows folder and then opening (and hence executing) that from within windows. 

Antiviruses in Linux are not really used to protect Linux machines as much as to avoid passing along infected files to windows machines. 

It's more likely for the opposite to occur, that a virus executed within windows modifies files in a Linux partition... Wubi is vulnerable to that as much as a standard dual boot installation (unless encrypted drives are used).

---

### Post by untermensch on 2008-06-01
I wonder as well about the viruses. Say you downloaded a windows virus in Linux. does the virus still run on the windows portion of the hard drive?

As to your question about your wireless card.. Linux can be difficult with some wireless cards, and an answer to your question would depend on which one you have.

I would also say [http://www.ss64.com/bash/](http://www.ss64.com/bash/) has a few bash commands, for simple things. and [http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/) has a pretty good list. 

hope that helps!

---

### Post by ago on 2008-06-01
> **untermensch said:**
> I wonder as well about the viruses. Say you downloaded a windows virus in Linux. does the virus still run on the windows portion of the hard drive?
No. Windows viruses do not run at all. But it is well possible to save the file on a windows partition. If you then access that file from windows then and only then will the virus run.

---

### Post by untermensch on 2008-06-01
ah ok. so unless you save it on windows, then run it on windows it wont do much of anything? Thank you very much!

---


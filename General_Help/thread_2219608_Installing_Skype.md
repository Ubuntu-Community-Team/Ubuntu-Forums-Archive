---
title: "Installing Skype"
date: 2014-04-24
forum: General Help
---

### Post by daniell59 on 2014-04-24
I would like to install skype. I did some reading on the subject. There seems to be a problem installing it on 64 bit. I would appreciate it if someone could give some direction on this.

Ubuntu 12.04 64

Thank you

---

### Post by Mark_Edwards on 2014-04-24
Hi, I just installed Ubuntu 14.04 x64 this evening, and installed Skype 4.2 literally 5 minutes ago.

I followed the alternative method in the article below which specifically checks for the architecture as part of the install.
[http://www.noobslab.com/2014/01/skype-released-new-version-install-in.html](http://www.noobslab.com/2014/01/skype-released-new-version-install-in.html)

 I just did the test call and it worked perfectly. I know your running 12.04 but hopefully either the official site, or the install method via the above link will work for you. I guess you can always test it and see what happens.

HTH :)

---

### Post by EmpireITtech on 2014-04-24
I've never had issues on either Ubuntu or Mint installing straight from the website >> [http://www.skype.com/en/download-skype/skype-for-computer/](http://www.skype.com/en/download-skype/skype-for-computer/)
Just choose the right version for you (12.04 multiarch) and you're off to the races

Let us know, thanks!

---

### Post by silex89 on 2014-04-24
Hi there! :)

There's also a version in the official repos, you can find it in the Ubuntu Software Centre and install it without having to download the package from the website. By using this method you ensure you have correct dependency resolving and will function better.

Best of Luck! :D

---

### Post by sammiev on 2014-04-24
> **silex89 said:**
> Hi there! :)

There's also a version in the official repos, you can find it in the Ubuntu Software Centre and install it without having to download the package from the website. By using this method you ensure you have correct dependency resolving and will function better.

Best of Luck! :D

+1

---

### Post by EmpireITtech on 2014-04-25
When I search in the Ubuntu Software Center (14.04) for "Skype" I find nothing...where are you finding it in there?

---

### Post by stalkingwolf on 2014-04-25
I usually install it from synaptic. makesure the partners repository is checked then reload .

---

### Post by WoodenWalker on 2014-04-25
Skype should be in the package manager. If not, I'm sure you can find a tarball for it out there some where. Those aren't too hard to install.

---

### Post by daniell59 on 2014-04-25
I found a site with easy to understand directions. I have not tried it yet.

[http://www.wikihow.com/Install-Skype-Using-Terminal-on-Ubuntu](http://www.wikihow.com/Install-Skype-Using-Terminal-on-Ubuntu)

---

### Post by EmpireITtech on 2014-04-25
Just as a note: if you install Skype from the download on their website, you probably will not have the Panel Tray Icon until you install this from the terminal >> sudo apt-get install sni-qt:i386
Or you can install the Skype Wrapper to integrate with your messaging menu >> [https://launchpad.net/~skype-wrapper/+archive/ppa](https://launchpad.net/~skype-wrapper/+archive/ppa)

---

### Post by LastDino on 2014-04-25
From my experience, I did face little trouble with Skype on x64 Ubuntu 14.04, but it was only some theme problem, functionality was intact. 

But yeah, install it from either default SM or Synaptic rather than getting it from their site.

---

### Post by jamesisin on 2014-04-25
I am using Skype on several 64 bit 14.04 machines.  I didn't realize it had been added to the repositories, so I've been using Skype's repo:

[http://jamesisin.com/a_high-tech_blech/index.php/2012/02/use-the-latest-skype-on-ubuntu/](http://jamesisin.com/a_high-tech_blech/index.php/2012/02/use-the-latest-skype-on-ubuntu/)

It may or may not be a more current version than that found in the Partner repository.

---

### Post by monkeybrain20122 on 2014-04-25
> **EmpireITtech said:**
> When I search in the Ubuntu Software Center (14.04) for "Skype" I find nothing...where are you finding it in there?

You need to enable "Canonical's partners" repository. In Software Centre go to Edit > Software Sources and check the box. You then restart the Software Centre and search for Skype you will find it there. I have been installing Skype like this since I started using Ubuntu (10.04), never had a problem.

---


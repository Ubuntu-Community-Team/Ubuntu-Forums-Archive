---
title: "Nightmare Software Center, why I cannot find apps/software?"
date: 2015-09-13
forum: General Help
---

### Post by greentea2 on 2015-09-13
Hello, 

I am quite new to Ubuntu and I really do not understand how the Software-Center works :confused:

Two examples: I have tried to find Skype by searching for the name "Skype", but also other key words - without results! Hence I understand that Skype is not availabe on the Software Center.  

For this reason I go to directly to the Skype website and download Skype for Ubuntu on that page. After downloading and ready to install Ubuntu refuses and says I should download directly from the software center and redirects me to a Skype download link in the software center. 

Identical case with Team Viewer. 

Can someone tell me what I am doing wrong?

Thanks in advance, 
Green Tea !

---

### Post by Bucky Ball on 2015-09-13
First, get rid of whatever you've installed from the Skype website. That is going to confuse things.

Open 'Software and Updates'> Other Software> and tick Canonical partners. Let it update. Install Skype from the official repositories. 

Avoid installing from third-parties when possible, which is usually.

PS: I don't see Team Viewer in the repositories.

---

### Post by greentea2 on 2015-09-13
> **Bucky Ball said:**
> First, get rid of whatever you've installed from the Skype website. That is going to confuse things.

Open 'Software and Updates'> Other Software> and tick Canonical partners. Let it update. Install Skype from the official repositories. 

Avoid installing from third-parties when possible, which is usually.

PS: I don't see Team Viewer in the repositories.

Hi @Bucky Ball, 

I completley agree with you, I prefer to download and update by the Ubuntu Software Center. But why the search function rarely find apps which are on the Center. 

And btw, Team View is also on the Software Center.

---

### Post by Bucky Ball on 2015-09-13
I don't prefer Software Centre. I don't have it installed. I use Synaptic Package Manager.

I don't have Team View in my repos, perhaps because I haven't added a PPA for it and haven't installed from a .deb file. I'd say this is how you'd install it, via the .deb file:

[https://www.teamviewer.com/en/download/linux.aspx](https://www.teamviewer.com/en/download/linux.aspx)

---

### Post by ian-weisser on 2015-09-13
> **greentea2 said:**
> But why the search function rarely find apps which are on the Center. 

Search can only see enabled sources. Once you enable it (add the repository or PPA), then Search can see it.
If a repository is not enabled, your system does not know the URL to find it, and cannot search it.

---


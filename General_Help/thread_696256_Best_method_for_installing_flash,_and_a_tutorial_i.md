---
title: "Best method for installing flash, and a tutorial if possible?"
date: 2008-02-13
forum: General Help
---

### Post by ogwilson on 2008-02-13
Well, I usually used to install flash via the firefox browser, but recently someone told me I should do it some other way just in case I use different browsers and whatnot. So how can I install flash as if it were to e enabled for system wide use and are there any tutorials on it?

---

### Post by xarquid on 2008-02-13
First, we need to make sure that the non-free (or "Multiverse" as Ubuntu refers to it) is added to your repository list.

> System -> Administration -> Synaptic Package Manager

To enable the Multiverse repository:

> Settings -> Repositories

In the Installation Media tab, click Add. There are three separate repositories; Gutsy (or Feisty/Hardy), Security Updates and Updates. Select each repository and check Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse). Ensure you click OK between each repository to save your changes.

**What we need to make SURE you check is MULTIVERSE.** And SAVE your changes.

You should now see those three repositories under Channels. Make sure Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse) appears under each repository.

To refresh the list of known packages (equivalent to apt-get update)

> Edit Menu -> Reload Package Information

Okay, now **EXIT** Synapic Package Manager. I just wanted you to do it this way to make sure we were on the same page. Sometimes when others have people append their /etc/apt/sources.list things are misunderstood. Checkings boxes in a GUI interface is more easily understood and straight forward (and less can go wrong.

Now please fire up your terminal:

> Applications > Accessories > Terminal

Please type:

> sudo apt-get update

Just for good measure.

And finally to install Flash to your system (across all browsers internally):

> apt-get install flashplugin-nonfree

I hope this helped.

Sincerely,

Craig Huffstetler / xarquid / xq

---

### Post by ogwilson on 2008-02-13
Thank you for the help. Well, I installed the one from adobe's site, but now I want to use this method that you've posted. Is there anyway to uninstall the method I used from adobe?

---


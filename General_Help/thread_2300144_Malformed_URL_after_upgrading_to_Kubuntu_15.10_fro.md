---
title: "Malformed URL after upgrading to Kubuntu 15.10 from 15.04"
date: 2015-10-23
forum: General Help
---

### Post by alexel2 on 2015-10-23
Hello, it's just as the title has said. After upgrading, there seems to be blank thumbnails appearing in the form of malformed URL's, and I can't seem to find the source of the problems within file managers. I think the problem is localised to my home directory since I backed it up before doing a clean install of 15.10, which I am using now (I wanted a fresh start + some preferences migrated; as a slightly more experienced user). After the current install was completed there were no problems, but once I merged the content folders from the back up to the current system, the malformed URL's as thumbnails started reappearing in the search bar. Would anyone kindly explain the problem to me and if possible help with a solution? If you need any further information please direct me on what, and how to obtain it - I will gladly comply.

Thanks!

---

### Post by miguel@scantec.pt on 2015-10-27
Same problem here since upgrading to 15.10. Clicking in search results (ex: pdf documents) besides the icon show with (?), the result on opening the file is a plasma error "malformed url"

---

### Post by alexel2 on 2015-11-13
Exactly. Sorry for the late reply, busy with work and studies. Did you find out how to resolve the problem?

---

### Post by matt_symes on 2015-11-14
Hi

> **alexel2 said:**
> Exactly. Sorry for the late reply, busy with work and studies. Did you find out how to resolve the problem?

Can you attach a screen shot to your next post as i'm not sure what you are explain and i think a screen shot may help.

Kind regards

---

### Post by alexel2 on 2015-11-17
> Can you attach a screen shot to your next post as i'm not sure what you are explain and i think a screen shot may help.

Kind regards 				 			  			   		 			 				 			 			 				[INDENT]If you believe everything you read, you better not read. ~ Japanese Proverb

If you don't read the newspaper, you're uninformed. If you read the newspaper, you're mis-informed. -     Mark Twain

[/INDENT]

[ATTACH=CONFIG]265636[/ATTACH][ATTACH=CONFIG]265639[/ATTACH][ATTACH=CONFIG]265638[/ATTACH]


Thank for your help. With each problem I become a better user and will someday be able to give back to the community.

---

### Post by matt_symes on 2015-11-18
Hi

Sorry for the late reply. Been a busy couple of days.

I cannot replicate this on a test machine so I'm not sure i can help you with this problem.

You may want to consider a fresh installation of 15.10 after backing up your files.

You may also want to post on the Kubuntu forms and see if they can help.

[https://www.kubuntuforums.net](https://www.kubuntuforums.net)

There is also an IRC channel and mailing lists where people may be able to help you.

[http://www.kubuntu.org/support](http://www.kubuntu.org/support)

Kind regards

---

### Post by SeijiSensei on 2015-11-18
Try this test.  Open a Konsole, then type these two commands at the "$" prompt:
```

cd
mv .kde .kde.old

```
Now log out and log back in.  KDE will rebuild your configuration with defaults.  Does your problem persist?

---


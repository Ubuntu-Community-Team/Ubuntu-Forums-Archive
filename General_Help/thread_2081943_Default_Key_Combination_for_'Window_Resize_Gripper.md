---
title: "Default Key Combination for 'Window Resize Grippers' ???"
date: 2012-11-08
forum: General Help
---

### Post by sorc3r3r on 2012-11-08
Hi
In recently upgraded from Ubuntu 11.04 to 11.10 through update manager and still discovering it's features and things. 

I accidentally hit some key combinations and I was given this 'Window Resize Grippers' on an active application window.

I haven't installed any software to tweak the Ubuntu environment. It's just a standard upgrade. 

I just dont know how 'Window Resize Grippers' popped up in the first place :confused:. Seems like a good option to me, so It would be helpful if any one can tell me how to bring about the 'Window Resize Grippers' whenever I want it . What is the default key combination?

I Google for the information and most of them talks about disabling it. A few of the articles I read asks me to install some software to enable it and add key combinations.
But, I suppose it's enabled by default, why else I was able to get it in the first place.

Just to have a visual clue of what I am talking about I am attaching a relevant image from Google search results.

Thanks in advance.

---

### Post by stinkeye on 2012-11-08
By default, for me grab handles is disabled.(12.04 and 12.10)
To see what yours is configured to, install ccsm.
In terminal...
```
sudo apt-get install compizconfig-settings-manager
```

To run, enter ccsm in the dash.
The plugin is at the bottom....**Unity MT Grab Handles**

---

### Post by sorc3r3r on 2012-11-08
Is it not possible without installing the CCSM? I read reviews about installing CCSM in UBUNTU 11.10 and found that most users who installed CCSM in 11.10 didn't have a pleasant experience.
Is there a work around?

---

### Post by stinkeye on 2012-11-08
Don't have 11.10 installed and things have changed.
Look in gconf-editor under /apps/compiz or apps/compiz-1
May have to install gconf-editor.

---


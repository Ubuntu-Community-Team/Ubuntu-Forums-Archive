---
title: "Firefox Won't Load Netflix Site But Chrome Will"
date: 2013-07-16
forum: General Help
---

### Post by Smallwheels on 2013-07-16
Hello folks. I've got 13.04. It was loaded today I used a Live USB for a few days and decided to go with it. The OS is the sole one on the computer. 

Firefox can't load the web site netflix.com. When I click enter or press the arrow to send the browser to the site it takes me to a page where it says server not found. It also changes the name in the address bar to movies.netflix.com. This address should take me to the log in page. 

To see if this was a Netflix problem I used my other computer to visit the same address. It works fine. Next I went back to Ubuntu and loaded Chrome. I used that browser to visit the site and I did get to the log in page. I typed in my information and it took me to the main page. 

I do not have Netflix loaded into my computer but I do sometimes want to see if a movie is available there while using the Ubuntu machine. What is wrong with Firefox? I would like to fix this.

Thank you.



Smallwheels

---

### Post by speartip on 2013-07-17
Netflix loads fine for me using Firefox 22.0.
Could you have some add-on enabled in Firefox, that is blocking the site?
Try disabling add-ons & try again.

---

### Post by Smallwheels on 2013-07-18
Thank you for the suggestion speartip. I did that and there was no effect. I then went through the Firefox Troubleshooting section and got to the point where I could totally reset Firefox. I did that and tried again without any add-ons or changes to any settings. The site still gives me the error "Server Not Found". It also still redirects me to movies.netflix.com. That doesn't work. 

In Chrome I can type movies.netflix.com and it takes me to movies.netflix.com/WiHome. 

One time earlier in the day I cleared the cache and cookies and tried the site and got to a Netflix page that said there was an error and to click a button. I clicked the button and it began the cycle of Server not found again. 

My machine is using Firefox 22. This is a new installation of Ubuntu with everything updated.

---

### Post by kurt18947 on 2013-07-18
I know nothing about Netflix but tried the above address.  I got to the member signin page even without disabling add-ons, only temporarily allowing in noscript.  Just a datapoint.  This is 13.10 & Firefox 23.

---

### Post by Smallwheels on 2013-07-18
I'm using four add-ons. Adblock; DoNotTrackMe, Video Download Helper, and Right to Click. It seems that I'm the only one with this problem right now. As I wrote earlier, I totally reset the browser and tried it with no add-ons and it didn't work. This is a perplexing problem for somebody who doesn't know the potential reasons this is happening. Since the browser takes me everywhere else I want to go, including posting here, I don't know what to say. 

I'll repeat that I'm using 13.04 that was installed this week. That might have a bearing on this or maybe not. 

When I used Chrome I got to the home page and logged in. I can see my movies listed and even my account. The site recognized me and my name is displayed on the top of the page. So it isn't a Netflix problem. 

Maybe it is a sub domain problem. Netflix takes me to a page with a sub domain. I haven't really noticed if the other sites I visit have them. Somebody give me an address of a working site with a sub domain address and I'll check that address in FF 22. If it doesn't work for me then that will be another clue to fixing this problem.

---

### Post by Smallwheels on 2013-07-18
I remembered that Wordpress sites at Wordpress.com are mostly sub domain named sites. I went there and found one. It worked fine from a link. Next?

---

### Post by Smallwheels on 2013-07-19
Do you think if I uninstalled Firefox and reinstalled it the problem might go away?

---

### Post by speartip on 2013-07-20
> **Smallwheels said:**
> Do you think if I uninstalled Firefox and reinstalled it the problem might go away?
You could try, but it would help if you deleted the .mozilla folder in your home folder as well, & start with a clean install in case some setting is the issue.

---

### Post by kurt18947 on 2013-07-20
> **speartip said:**
> You could try, but it would help if you deleted the .mozilla folder in your home folder as well, & start with a clean install in case some setting is the issue.

Along similar lines, if I have a problem like this and don't want to lose all the settings & data in my .mozilla folder, I've created a temporary user account and tried with that.  No add-ons, no nothing just create a new user and try to load the problem page.

---


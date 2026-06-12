---
title: "weird javascript problem"
date: 2008-04-14
forum: General Help
---

### Post by fouadk on 2008-04-14
hi everyone

 i am having a weird problem....facebook worked fine until yesterday....i havent done anything....
it just tell me that javascript is disabled although it isnt....

it works well on windows,,,,

i have upgraded or done anything out of the ordinary...

please help

thanks in advance

---

### Post by y-lee on 2008-04-14
What web browser are you using?

---

### Post by fouadk on 2008-04-14
firefox 2 does not work...firefox 3 same ****....konqueror also....firefox runnning on wine same prob...

but firefox running on widows or IE on windows...no problem....

that happened out of no where...

---

### Post by y-lee on 2008-04-14
hmm very odd esp since it is affecting several different browsers.** I really don't know the cause** but do ya get any errors when you open the browser say firefox in a terminal and go to facebook?

Have you tried a new profile for firefox or firefoxes safe mode? (if ya don't know how either man firefox or post back)

Edit: Also is this just a problem with js in facebook or does it also fail to work on other websites using javescript?

---

### Post by fouadk on 2008-04-14
weird....some other website requiring javascript works , some others dont...

i also have a weird issue too....the nvidia page does not work also under ubuntu....

---

### Post by y-lee on 2008-04-14
The nvida page looks like it uses flash to me. It is working for me btw. Do you have flash installed??

---

### Post by fouadk on 2008-04-14
yep i have flash installed....it does not respond at all....its like the site is down but in reality it isnt...it works well on windows on another local machine and on the same machine....

concerning facebook.....i have reinstalled java and created a new profile and delete the cache and cookies and everything,,,,nothing at all

---

### Post by y-lee on 2008-04-14
I honestly don't know but java and javascript are two different things. javascript as far as I know is build into the web browsers and that is why it is odd your problem is occurring on multiple web browsers. I'm hoping somebody sees this that does know what is going on, I googled it but saw nothing that helped tho maybe I didn't look long enough. :confused:

Sorry I can't help more :(

---

### Post by fouadk on 2008-04-14
im really confused...hope a clean installation of hardy will fix everything...

Do u have any idea if hardy will support broadcom wireless cards by default coz im running now with ndiswraper and im suspecting its the problem behind nvidia...

Do u know where i can find a list of the newly supported hardware in hardy?

Thanks again

---

### Post by y-lee on 2008-04-14
I would assume hardy supports everything gusty does hardware wise, maybe more but I don't know. As to the broadcom wireless card with the beta version

> If you have a Broadcom Wireless card, you will get a [WWW] Jockey crash at startup. Please upgrade to a newer version after installation.

See [HardyHeron/Beta]("https://wiki.ubuntu.com/HardyHeron/Beta"), hopefully that will be resolved before the release. But I would probably expect some kind of problems :(. there is a section of this forum that is devoted to hardy testing and hardy issues you might have more luck asking your hardware questions there. I use Dapper but I am upgrading to hardy when it is released but I don't use wireless on my desktop and don't have a laptop :(

---

### Post by lamps06 on 2008-06-03
I am having the same issues with Javascript.  I was trying to register for a website and it would not let me because it told me I did not have javascript enabled in Firefox 3.0 RC 1 but I do have javascript enabled.  I had to boot into Windows XP and use Firefox 2.0 to register for the website.

I have also noticed that if I go to the Friends section of my Netflix account none of their movies show up within their windows, the panes are just blank.  Has anyone determined what is going on?

---

### Post by fouadk on 2008-06-03
i was able to fix that problem by using openDNS...the ips pf openDNS are 

208.67.222.222
208.67.220.220 

point ubuntu to use these DNS and hope your problem will get fixed like mine was fixed....

---


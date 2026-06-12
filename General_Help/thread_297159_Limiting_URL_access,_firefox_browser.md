---
title: "Limiting URL access, firefox browser"
date: 2006-11-10
forum: General Help
---

### Post by a.d.gardiner on 2006-11-10
Hi guys,

I've been struggling with this for a few days now.

Basically what im trying to do is create a very limited list of URL's that firefox will be able browse to. For example block everthing but 'www.bbc.co.uk' and 'www.ubuntu.com'.

I don't think I really need the kind of complex filtering solution offered by the likes of dansguardian or squidguard etc.

I've been through the forums and extensive searches of the net, but can't find anything this simple. Simply id like firefox to work similar to opera in kiosk mode but only be able to access say 10 or 15 urls. The machine will be sat on in a staff area of a sales floor in a shop and I only want staff to be able to access a very limited few sites which they will find useful.

Any ideas?

;)

---

### Post by msak007 on 2006-11-11
Firefox has several kiosk extensions but I've never used any of them so I can't tell you how well they work. I can't link to any of them now because for some reason the Mozilla extensions site seems to be down. I know you said you didn't want to go the route of dansguardian / squidguard, but I think that might be the best option and is not really that hard to set up - there are plenty of guides to walk you through it. Set up a proxy, hard code it and lock it in Firefox so users on the comp can't bypass it, and then create a whitelist of sites they're allowed to visit.

---

### Post by stream303 on 2006-11-11
Try this:

Remove the ability to use DNS and rely solely upon what can be found in the /etc/hosts file.  (talk about old-school, but that's the way it was done before dns...)

1) edit your **/etc/nsswitch.con**f file and change the line that reads:
[B]
hosts: files dns[/B]

and change it to

**hosts: files**

2) Now edit your **/etc/hosts** file and just add the sites ip address something like this:

123.45.67.89  [www.bbc.co.uk](www.bbc.co.uk)
345.67.89.10  [www.ubuntu.com](www.ubuntu.com)

Obviously change the ip addresses to the real ones...

Editing the /etc/nsswitch.conf file like this makes the system only look at the /etc/hosts file for nameserving.

---

### Post by a.d.gardiner on 2006-11-11
8) Many thanks guys..

I got squidguard up and running good last night.. but the company I work for are really reluctant to have another machine in the office dedicated to something they don't understand. lol. We need quite a complicated set of instructions for different users aswell if that was to be the case. I know it can be run on an individual machine but Im going out on a limb here getting linux into the place i work already. Plus it is essentially just 2 machines that need completely locking down to a few addresses and the removal of DNS seems like a good solution to me.

The only thing Im trying to do now is replace the  firefox can't find server error page with something else so when you ask for a page not in the list it is more apparant that it is essentially denyed rather than inacessible.

old school!

much appreciated :p

---

### Post by msak007 on 2006-11-11
Wow stream303 that's a pretty cool trick I didn't know about. Maybe that is easier :). It effectively serves the same purpose of  whitelisting specific sites and only requires editing 2 files.

---


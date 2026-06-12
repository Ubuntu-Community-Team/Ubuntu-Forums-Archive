---
title: "Cannot change default email program"
date: 2008-02-03
forum: General Help
---

### Post by Packrat73 on 2008-02-03
I am using Firefox as my browser and want to use Evolution as my default program. But when clicking a mailto link in FF it brings up gmail webpage. I want it to bring up Evolution.

I have evolution set up as default under system-preferences-preferred applicatoins, but no matter what I change it to (evolution or thunderbird) it still sends me to gmail.com when I click a mailto link.


Thanks for any help.

---

### Post by y-lee on 2008-02-03
I am going to assume for now this is a firefox issue.

First open Firefox and type **about:config** in the address bar

type in the filter text box :

```
network.protocol-handler.external.mailto
```

is this set to true? 

if not right click it and choose toggle to change it to true. restart Firefox and try now.

if it was true or the change didn't work once again go back to the about:config thing and

right-click a blank spot in the window and select **New**--> **String**

Name the string as follows:

```
network.protocol-handler.app.mailto 
```

The value of the string should be:

```
 /usr/bin/evolution
```

Once you have done this click OK and restart Firefox. Now try and see if it works.

---

### Post by dcstar on 2008-02-04
> **Packrat73 said:**
> I am using Firefox as my browser and want to use Evolution as my default program. But when clicking a mailto link in FF it brings up gmail webpage. I want it to bring up Evolution.

I have evolution set up as default under system-preferences-preferred applicatoins, but no matter what I change it to (evolution or thunderbird) it still sends me to gmail.com when I click a mailto link.


Thanks for any help.

Also check: Applications-System Tools-Configuration Editor-/desktop/gnome/url-handlers/mailto

---

### Post by Packrat73 on 2008-02-04
I tried all that was stated and it still sends me to gmail.com

Any other ideas? I am at a loss.

Thanks for the replies.

---

### Post by y-lee on 2008-02-04
Strange

Has Firefox always did this or is this something new?

You don't by any chance have any extensions installed in firefox pertaining to either gmail or web based e-mail? This includes greasemonkey scripts stylish scripts. If so disable them restart firefox and try again.

If that doesn't work, lets see if your firefox user  profile is messed up

```
firefox -P
```

This starts firefoxs profile manager, you will be prompted to create a new profile. Choose that option and give it a new name like debug or something. After doing that start firefox  now try the mail to links. If they work now  we will try to figure out how to fix your old profile

**EDIT: **One more question, does clicking a mailto link or e-mail address in an application other than firefox, say tomboy still open gmail instead of gnome. If so it is probably not a fireox issue but a gnome one. let us know.

---

### Post by Packrat73 on 2008-02-04
Nevermind, I found the problem. I am using better gmail 2 plugin in FF. the problem was that by default better gmail 2 forces you to use gmail.

---

### Post by y-lee on 2008-02-04
> **Packrat73 said:**
> Nevermind, I found the problem. I am using better gmail 2 plugin in FF. the problem was that by default better gmail 2 forces you to use gmail.

Glad ya found the problem. Mark it as solved please. I love firefox addons too, btw, but sometimes they can cause ya problems esp if you are like me and have about a hundred of  them. :lolflag:

---


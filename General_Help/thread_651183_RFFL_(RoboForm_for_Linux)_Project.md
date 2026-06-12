---
title: "RFFL (RoboForm for Linux) Project"
date: 2007-12-27
forum: General Help
---

### Post by alex_yen on 2007-12-27
Hello all!

I use RoboForm program on my windows computer and very-very like it. Anyway, I have an Ubuntu machine at home and I really want to have a RoboForm extention there too. But, unfortunately, I saw on the RoboForm site, that they don't want to create a Linux version of a program!

As a result, I decided to check out - am I alone on this world? Only me so desperate about this?

People! If you are in love with RoboForm as I am, post here!

This will create some talks and some ideas. Maybe this will lead to a new extension for FireFox that will have the same usability as RoboForm, but will be trans-platform instead.

P.S.:
Yes, I know that I can use wine to simulate windows firefox, but I want it on the Linux firefox without troubles around
Yes, I know that there are some similar programs on linux (keypassx, code in monkeygrease and so on), but they are not that good

---

### Post by alex_yen on 2007-12-27
My demands on RFFL Extension:
1. When I have a site with login, RFFL will suggest to me to save the login name (for example, Ubuntu login)
2. When I want to login to Ubuntu site, I just click on 'Ubuntu login' and it automatically redirects me to the site of Ubuntu.com and logins in
3. It will save forms
4. When I want to fill form, I just click on 'Ubuntu form' on my menu (for example) and it will redirect me to the site, fill the form and press enter
5. I can have unlimited profiles,passcards, logins, forms, identities
6. I can organize,edit, print passcards, profiles, etc
7. It will generate passwords
8. It will save all the information in the scripted manner
9. It will AutoFill fields only if I want to

There is an extension, that can record macro of what you do, but it has its limitations and not so convinient

---

### Post by rebshalom on 2008-01-30
I contacted Roboform yesterday. They said that they have no plans for a Linux version and that they do not have open source code.  I guess that means somebody will have to build a product from scratch.

---

### Post by jaygo on 2008-01-30
it would probably be useful to put any such efforts into the existing keepassx project which is already half way there. Its root project, keepass ([http://keepass.info](http://keepass.info)), is now built on mono, which apparently will eventually let it run in Linux natively. That might also be a good option. For now, keepassx is a start, along with the firefox plugin sxipper.

---

### Post by wjgray on 2008-02-15
I know this thread is incredibly old, bu I was "in search of..." the same thing.  Believe it or not, the ONLY thing holding me back from being an Ubuntu user is the lack of Roboform-like capability.  For me, it is NOT the password management.  If it were just that then KeePass would work perfectly.  What it IS is the identity management features.  It store my addresses, my phone numbers, my credit cards, bank accounts, wife's info, son's info, .....  It is my identity manager.  Whenever a site is asking for any info I can use RF to use the proper identity and submit the proper info lickety-split.  Anyway, I guess I am responding to this in hopes that it will ignite someone's creative mojo and gets to work on a project that is sorely needed for *nix.  Hard to believe that everything falls short.

BUMP.

---

### Post by DEinspanjer on 2008-02-21
Exactly the same boat.  It frustrates me that Siber isn't interested in porting to Linux or at the very least helping to get a tight Wine integration working.

I think that with the right developers, it might be possible to get the native Roboform extension talking to a Wine based dll.  It will take a bit of mojo though.

There really just isn't anything else out there with the feature set that Roboform has, but if one of the other password management projects that supports Linux does make the push to get those features in, I'll certainly move over to them rather than having to fight this battle.

---

### Post by Vorless DarkChaos on 2008-03-07
[http://nimishbatra.wordpress.com/2007/06/19/roboform-linux/]("http://nimishbatra.wordpress.com/2007/06/19/roboform-linux/")

answer is there

---

### Post by LOBONCA on 2008-03-08
This information may be helpful:
[http://www.cyberciti.biz/tips/personal-password-manager-linux-windows-os-x.html](http://www.cyberciti.biz/tips/personal-password-manager-linux-windows-os-x.html)

In my search for a RoboForm replacement I also found Handy Password manager:
[http://www.handypassword.com/password-manager-linux.shtml](http://www.handypassword.com/password-manager-linux.shtml)
which looks a lot like RoboForm and says it runs under Linux and Windows.

I have not tried it yet. If anyone knows anything about it or has experience, please post about it.

---

### Post by Yochanan on 2008-04-03
Handy Password is not yet available for Linux. [They say it's on it's way](http://www.handypassword.com/password-manager-linux.shtml), and you can vote for it and other features [here](http://www.handypassword.com/coming-soon.shtml).

---

### Post by metrocard on 2008-04-20
I've been checking out what's been happening to [Sxipper]("http://www.sxipper.com") every few months, and with their 2.0 release, they now offer importing of RoboForm passcards and identities and offer (plain text) import/export of your Sxipper data. You also don't have to have a login to their servers to use their Firefox extension anymore.

Having imported my Roboform passcards into Sxipper, I found that some did not come over automatically, which I was able to resolve by using Roboform to login to the missing sites, at which point Sxipper would prompt to store the password.

Overall, with this new functionality I'm getting to be pretty happy with Sxipper on both Windows and Linux as a Roboform replacement.

---

### Post by Vorless DarkChaos on 2008-04-21
> **Vorless DarkChaos said:**
> [http://nimishbatra.wordpress.com/2007/06/19/roboform-linux/]("http://nimishbatra.wordpress.com/2007/06/19/roboform-linux/")

answer is there

This is from [http://nimishbatra.wordpress.com/2007/06/19/roboform-linux/]("http://nimishbatra.wordpress.com/2007/06/19/roboform-linux/")

1. Install Wine.

2. Install IE 6 using IEs4Linux.

3. Download Roboform [roboform.com], and run it by accessing it through the IE6 address bar [pretend as if it was Windows Explorer... use the Open dialog or the Address bar].

4. Once installed, copy your “My Roboform Data” folder from My Documents (or wherever) on your Windows partition, into the folder specified by Roboform @ Linux.

5. Use the exact same method as #3 for downloading and installing Firefox ([www.download.com](www.download.com)) under Wine, and download and install Roboform’s Firefox adapter (roboform.com).

---

### Post by limejuice on 2008-05-01
I just made the leap to Unbuntu, and overall it's been a great experience.  For me, like many people, the browser is the main OS, not Windows or Ubuntu, so it's great that Firefox and related plugins like flash were very easy to get running on Ubuntu 8.0.4.

My biggest pain point is I miss roboform.  I am a heavy roboform user with 500+ logins and also a couple identities I use to keep track of all my login passwords and fill in address forms. 

As someone mentioned in earlier comment, filling in login/password isn't that complicated, but filling in address/contact/email information/credit card information in forms is complicated, and roboform does it very well.  I also use it at my work to fill in shipping information for different destinations.

I guess I'll try this sxipper and keepassx. On the face of it, it looks like only sxipper has integration with firefox, so I guess I'll try that first.

Sxipper is closed source I think.  Also, I'm not sure how secure Sxipper is running inside firefox. It's pretty new, so it probably has security flaws. I know of no open source program that does what roboform and sxipper do. 

I like Keepassx security, esp. the option to use a key on USB flash stick rather than or in conjuction with typing a master password, but it doesn't integrate with firefox.

Keeping track of passwords and identity information is really critical part, and it's also important that the security of the information is bulletproof; Therefore, I would prefer an open source solution where the code can be reviewed and hacked on by the linux community.

---

### Post by Vorless DarkChaos on 2008-05-27
i have no problems using robo form on ubuntu

---

### Post by Yochanan on 2008-05-27
Sxipper supports importing Roboform Passcards now!

---

### Post by sicofante on 2008-06-02
> **Yochanan said:**
> Sxipper supports importing Roboform Passcards now!
Yes, but it still does not support login into sites with three or more fields than the ordinary username/password pair. I have a number of these and there seems to be no substitute for Roboform in that area.

Also, I have imported 413 passcards and Sxipper says it succeeded with 370. What about the rest? No clue. :(

Using the built-in Firefox password manager is a lazy and wrong move.

Lack of Roboform functionality in Linux is probably the #1 issue keeping me from fully switching.

---

### Post by Andre-D on 2008-06-18
Well, I am fed-up with Roboform's arrogance - "we dont have plans for linux"  BAH ! _ "you are married to M$ and in love with .NOT" (.net)

this is why I change to SXipper everywhere, I need a company that understands the meaning of the word "freedom"

---

### Post by sicofante on 2008-06-18
Me too hate Roboform's "no-Linux" stance, although I can understand it from a business point of view. I just can't grasp why the Roboform approach isn't supported by anyone else. Instead of treating passwords as such, Roboform deals with everything with the form-filling mentality, which is right IMO. The username/password pair is not right, since most websites include things like "remember me" boxes and stuff that is worth saving. It isn't that hard isn't it?

---

### Post by Dale Sexton on 2008-06-23
> **Vorless DarkChaos said:**
> 

3. Download Roboform [roboform.com], and run it by accessing it through the IE6 address bar [pretend as if it was Windows Explorer... use the Open dialog or the Address bar].

I'm not understanding this part of the instructions. Am I to put the location of the program from the desktop as the address? If so, I'm not sure about linux addresses.

Oh! I didn't know you could do that. That's not how I installed it before on windows. So far so good. Now I need to get it on firefox.

---

### Post by Dale Sexton on 2008-06-23
> **Vorless DarkChaos said:**
> [http://nimishbatra.wordpress.com/2007/06/19/roboform-linux/]("http://nimishbatra.wordpress.com/2007/06/19/roboform-linux/")

answer is there

Works great! I was even able to use this procedure to make Instant Buzz work.

---

### Post by Psipherious on 2008-07-18
While I definitely agree that it sucks that RoboForm is anti-linux I'm not sure if I trust this Sxnipper program, if you read the reviews on the FF plugins page: [https://addons.mozilla.org/en-US/firefox/reviews/display/4865?show=100](https://addons.mozilla.org/en-US/firefox/reviews/display/4865?show=100)

**A lot** of people on there complain about security issues, mentions of the software phoning home and whatnot.

It's nice that it's free, if only it was open source and could be verified to be more secure than many are claiming it to not be.

---

### Post by madblueimp on 2008-07-18
In my opinion [Secure Login](http://securelogin.mozdev.org/) and [Autofill Forms](http://autofillforms.mozdev.org/) are a good replacement for Roboform.

[see my post on the same topic on the mozillazine forums](http://forums.mozillazine.org/viewtopic.php?f=19&t=615251&p=3886345#p3886345)

---

### Post by sicofante on 2008-07-18
@madblueimp: You've got the idea and your extensions are good but have a serious user interaction design problem. In order to "compete" with Roboform you should think of addressing the following and probably more:

1- Merge the two extensions into a single one.
2- Remove or hide the regular expression thingy. No one except very skilled computer power users will ever understand regular expressions.
3- Prompt the user to save currently fillled forms (in a new website) and prompt the user to fill the current known fields (in an already "registered" website)
4- Save different logins for the same website (like login into different gmail accounts, for instance), with meaningful user-editable names. The different login names for a single website are too many times meaningless (I think of bank account numbers for instance).
5- Name the fields to be filled manually with meaningful names (maybe the text before the textfield?). The HTML names behind the name don't mean a thing to an ordinary user.
6- EDIT: The most important one: make the extensions work right out of the box. They don't do anything if not configured properly and the user is forced to a thorough research.

These are just but a few usability issues. I would be really happy to help you with the user interaction design, if you will. I'm pretty rusty when it comes to coding (too many years without actively doing it), but I can speak "programmerish". Don't hesitate to PM me if you want.

(Yes I'm the same guy ;))

---

### Post by madblueimp on 2008-07-19
> **sicofante said:**
> 1- Merge the two extensions into a single one.
I've developed [Secure Login]("http://securelogin.mozdev.org/") as an extension to Firefox integrated password manager.
[Autofill Forms]("http://autofillforms.mozdev.org/") has been developed to be able to fill out additional fields that Firefox password manager doesn't store in its database.
It was a deliberate decision to create two independent add-ons.

> **sicofante said:**
> 2- Remove or hide the regular expression thingy. No one except very skilled computer power users will ever understand regular expressions.
That's what the Simple Interface of [Autofill Forms]("http://autofillforms.mozdev.org/") is for. No need to understand regular expressions to be able to use it.
There is also a rule editor if you want to create your own rules but don't know anything about regular expressions.
The regular expression capability makes [Autofill Forms]("http://autofillforms.mozdev.org/") a very powerful tool for advanced users.
[Autofill Forms]("http://autofillforms.mozdev.org/") may not be the most intuitive autofill application, but it's definitely the most customizable one.

> **sicofante said:**
> 3- Prompt the user to save currently fillled forms (in a new website) and prompt the user to fill the current known fields (in an already "registered" website)
Via the context menu of form fields it's very easy to create new rules or add complete forms as profiles.
[Autofill Forms]("http://autofillforms.mozdev.org/") needs documentation, but it is not that complicated to use.

> **sicofante said:**
> 4- Save different logins for the same website (like login into different gmail accounts, for instance), with meaningful user-editable names. The different login names for a single website are too many times meaningless (I think of bank account numbers for instance).
[Secure Login]("http://securelogin.mozdev.org/") will use the data available from Firefox password manager - nothing more.

> **sicofante said:**
> 5- Name the fields to be filled manually with meaningful names (maybe the text before the textfield?). The HTML names behind the name don't mean a thing to an ordinary user.
Most autofill applications (including Google Autofill) use the HTML name attributes of form fields to identify them because it's the most reliable source. [Autofill Forms]("http://autofillforms.mozdev.org/") also makes use of form field labels, but too many web forms don't make use of the HTML label element. [Autofill Forms]("http://autofillforms.mozdev.org/") also features an option to use the text in front (or behind in case of checkboxes and radio buttons), but it's not reliable to use because there is no relation between the text and the form field.

> **sicofante said:**
> 6- EDIT: The most important one: make the extensions work right out of the box. They don't do anything if not configured properly and the user is forced to a thorough research.
[Secure Login]("http://securelogin.mozdev.org/") definitely works out of the box for any login forms that Firefox password manager stores login information for.
[Autofill Forms]("http://autofillforms.mozdev.org/") works out of the box for many other web forms, e.g. registration forms (after inserting your data into the Simple settings dialog).


[Secure Login]("http://securelogin.mozdev.org/") is feature complete. It's an add-on to Firefox password manager and makes the login process more comfortable and secure.

I agree that [Autofill Forms]("http://autofillforms.mozdev.org/") could need some improvements regarding the user interface.
Though what it needs most is documentation.

[Autofill Forms]("http://autofillforms.mozdev.org/") can be used by the average user via the Simple settings dialog and the context menu of form fields.
The advanced capabilities of [Autofill Forms]("http://autofillforms.mozdev.org/") address the power user - making it the most customizable form filler available.

I've never used Roboform myself and I've not developed [Secure Login]("http://securelogin.mozdev.org/") and [Autofill Forms]("http://autofillforms.mozdev.org/") as a replacement for this program.

I'm sorry if I'm disappointing you here regarding the topic - but it is not my intention to create a "Roboform for Linux".
Judging from the description on the Roboform homepage I just think that with [Secure Login]("http://securelogin.mozdev.org/") and [Autofill Forms]("http://autofillforms.mozdev.org/") you have an alternative which is available for the GNU/Linux platform and free open source software besides.

---

### Post by sicofante on 2008-07-19
I've replied in the MozillaZine forums.

---


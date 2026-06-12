---
title: "Jammy: Why some package do not get updated ?"
date: 2022-09-26
forum: General Help
---

### Post by georgesgiralt on 2022-09-26
Hello all !
On my newly installed Jammy laptop, I've a set of 5 packages which are said "not updated" since more than a week. 
```

$sudo apt upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Lecture des informations d'état... Fait      
Calcul de la mise à jour... Fait
Les paquets suivants ont été conservés*:
  libspeechd2 python3-speechd speech-dispatcher speech-dispatcher-audio-plugins speech-dispatcher-espeak-ng
0 mis à jour, 0 nouvellement installés, 0 à enlever et 5 non mis à jour.
$

```
At first I thought that some dependency was not met and apt waited for a packet to be released, but I searched the dependencies for libspeechd2 and found it has all of them satisfied. I did the same for the python3-speechd and it was the same. 
So I wonder if I have an underlying problem with my packages pile and/or apt databases? 
I would like to have some help on this matter, please....
Have a nice and bright day !

---

### Post by Impavidus on 2022-09-26
It looks like phased updates. They have been around for some years, but now that apt deals with them too, it appears to confuse a lot of people. The forum is full of threads about this.

Just wait. If there are no problems with this update, you'll get it automatically at some point. If there are problems, you'll be glad that you didn't get it.

---

### Post by georgesgiralt on 2022-09-26
Thank you for your answer. But Synaptic is willing to install them ! So I wonder what the problem is/can be ?

---

### Post by ActionParsnip on 2022-09-26
The dependency packages are not met for those packages. Eg:

Package A is installed at version 1.0
Package B is install at version 1.0 and depends on package A being at version 1.0
Package A is updated to version 2.0 and needs package B to be at version 2.0 but package B is not at version 2.0....yet. It is held back
later
.
.
Package B is updated to version 2.0 and so now the dependency is met and package A will install at version 2.0 as well as package B at version 2.0

---

### Post by georgesgiralt on 2022-09-26
And how come Synaptic tells me I can update the packages ? Dependencies are not met even if it is apt or Synaptic I use to show/install packages ?
I'm more and more puzzled.

---

### Post by Irihapeti on 2022-09-26
This does seem to be happening much more in jammy than it did in previous releases. In fact, from what I recall, it was only during the development/pre-release phase that updates would be held back. I've been wanting to ask the same question: why? What's changed?

---

### Post by Impavidus on 2022-09-26
[Read about phased updates here.](https://wiki.ubuntu.com/PhasedUpdates) They have been around for a decade, but originally only update manager used them. The apt command line tool just installed all available updates. Now apt also takes phased updates into account, but if you ask specifically for this update to be installed, apt will comply. So does synaptic.

Confusingly, apt says that some packages have been held back, but doesn't say whether this is because of dependency issues or because of phased updates. But if you want to check:```
$ apt-cache policy libspeechd2
libspeechd2:
  Installed: 0.11.1-1ubuntu1
  Candidate: 0.11.1-1ubuntu2
  Version table:
     0.11.1-1ubuntu2 500 (phased 20%)
        500 http://nl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
 *** 0.11.1-1ubuntu1 100
        100 /var/lib/dpkg/status
     0.11.1-1 500
        500 http://nl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
```See? Phased 20%, so it's coming.

---

### Post by &amp;KyT$0P# on 2022-09-26
> **Irihapeti said:**
> This does seem to be happening much more in jammy than it did in previous releases. ... why? What's changed?

Phased updates [were introduced to apt in 21.04]("https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345"), but 21.04 and 21.10 apt had a pinning-based implementation that was mostly opaque to the user.  Some time after 22.04 was released, 22.04's apt was updated with a new phased updates implementation that instead has packages "kept back", which as a side effect makes the not-yet-phased-in phased updates visible to the user.  It is *that* change that prompted all these threads, since the reason for the keep back is not stated and is not obvious (not even to me, even knowing about this: I always check [here]("https://people.canonical.com/~ubuntu-archive/phased-updates.html") before giving that answer to these threads).

---

### Post by ne29914 on 2022-09-26
Phased upgrades seem to be a wet dream for sysadmins, but are inconprehensible, confusing and useless for normal desktop users.
I find the decision to take this step highly questionable and a risk of losing the Ubuntu desktop user community/support. If it ain't broke, don't fix it.
Sysadmins have lots of tools available already, why foist this on normal users?
@Impavidus has some kind of information workaround, but why do I have to do something extra?
The beauty of Synaptic was its simplicity.

---

### Post by ian-weisser on 2022-09-26
> **Irihapeti said:**
> This does seem to be happening much more in jammy than it did in previous releases.

There are always a lot of SRUs during the first cycle after an LTS release. Perhaps Phased Updates has highlighted all those SRUs for us for the first time.

We can see this by comparing to 22.04 complaints to 21.04 complaints. Same apt feature, but almost no questions about it; it was almost completely unnoticed. Combination of smaller user base and fewer SRUs.

---

### Post by ne29914 on 2022-09-26
> **ian-weisser said:**
> There are always a lot of SRUs during the first cycle after an LTS release. Perhaps Phased Updates has highlighted all those SRUs for us for the first time.
We're now almost in October. I wouldn't say that 22.04 is dew-fresh...

---

### Post by ian-weisser on 2022-09-26
> **ne29914 said:**
> We're now almost in October. I wouldn't say that 22.04 is dew-fresh...

The process of troubleshooting, reporting, verifying, and upstreaming a bug takes a great deal of time and effort, as does the process of designing and creating the patches, identifying which patches can/should be applied to the current release, and then repackaging, testing, and finally distributing. Four to five months is not a surprise at all.

Of course, it could go faster: A few community members who decide to volunteer to help a bit more could really make a difference.

---

### Post by &amp;KyT$0P# on 2022-09-26
> **ne29914 said:**
> Phased upgrades seem to be a wet dream for sysadmins, but are inconprehensible, confusing and useless for normal desktop users.
I find the decision to take this step highly questionable and a risk of losing the Ubuntu desktop user community/support. If it ain't broke, don't fix it.
Sysadmins have lots of tools available already, why foist this on normal users?
@Impavidus has some kind of information workaround, but why do I have to do something extra?
The beauty of Synaptic was its simplicity.

ne29914, as noted in the link I posted in your own thread about this, you can configure apt to restore the old behavior completely disabling apt's phased update support.

---

### Post by ne29914 on 2022-09-26
@halogen2, I assume you are referring to this link:

[https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345/33](https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345/33)

That's a stomach-churning, but also hilarious piece of double-talk and confusion, ending up in a discussion about the meaning of always/never/true/false.

But it does not clarify how to set the Synaptic behaviour.

I think some corrective action is needed. But I know: writing documentations and Wikis is boooring.

---

### Post by &amp;KyT$0P# on 2022-09-26
> **ne29914 said:**
> @halogen2, I assume you are referring to this link:

[https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345/33](https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345/33)

Yes, that one.

> it does not clarify how to set the Synaptic behaviour.

It's controlled at the apt layer, so you set it by the apt configuration described in the first post of that thread: create a file [FONT=Courier New]/etc/apt/apt.conf.d/90disable-phased-updates[/FONT] with the following contents -
```
APT {
  Get {
    Always-Include-Phased-Updates true;
  }
}
```

Tested this in a 22.04 VM and now when I run Synaptic and select "Mark All Upgrades", it now does literally that, the phasing of updates is ignored just like in 20.04 and prior.

---

### Post by ne29914 on 2022-09-26
> **halogen2 said:**
> Yes, that one.



It's controlled at the apt layer, so you set it by the apt configuration described in the first post of that thread: create a file [FONT=Courier New]/etc/apt/apt.conf.d/90disable-phased-updates[/FONT] with the following contents -
```
APT {
  Get {
    Always-Include-Phased-Updates true;
  }
}
```

Tested this in a 22.04 VM and now when I run Synaptic and select "Mark All Upgrades", it now does literally that, the phasing of updates is ignored just like in 20.04 and prior.

Thank You. That actually worked, and as a nice side-effect, the tedious "mtd" error during booting disappeared.

But please don't ever link to that thread again. It's total geek-speak with no information value at all to users.
And the logic of always/never/enable/disable/true/false still eludes me. A developer apparently needs to use inverted/inverted/inverted/inverted/inverted logic.

---

### Post by Irihapeti on 2022-09-26
It's interesting to see that the "updates held back" message applies to two completely different issues.

As I recall it, during the development stage, if you get a partial upgrade offered, you accept it at your own risk, presumably because important dependencies may be still to come. So I found the new behaviour a bit concerning: was I supposed to wait until everything was ready, or what? I think this part could have been made clearer.

But maybe that's one of the consequences of going LTS to LTS &#8211; you don't get the advisories relating to the interim releases. (Or maybe I'm wrong &#8211; it wouldn't be the first time.)

---

### Post by ne29914 on 2022-09-26
> **Irihapeti said:**
> 
But maybe that's one of the consequences of going LTS to LTS &#8211; you don't get the advisories relating to the interim releases. (Or maybe I'm wrong &#8211; it wouldn't be the first time.)
No, I think you're absolutely right. Why should users _not_ infected with "upgradeitis" be subjected to this?
Instead of making "phased upgrades" the default, it would be better for the "sysadmin" type of users to "opt-in" by letting _them_ create a new file in /etc/apt/apt-conf.d. Or?
This is the most ill-advised change to Synaptic I've ever seen, and it's spreading uncertainty everywhere. It's pure Microsoft thinking: "_We_ know what's best for you."

---

### Post by &amp;KyT$0P# on 2022-09-26
> **ne29914 said:**
> Thank You. That actually worked, 

You're welcome.

> But please don't ever link to that thread again. It's total geek-speak with no information value at all to users.

What link would you suggest I use when replying to non-advanced-users about this?

---

### Post by ne29914 on 2022-09-26
> **halogen2 said:**
> You're welcome.

What link would you suggest I use when replying to non-advanced-users about this?
Your own (#15 in this thread).

---

### Post by QIII on 2022-09-26
@ne29914 

Please curb your attitude and don't use childish abbreviations like "M$" here,  You gain no cred ... and it is against the Forums Rules (please see my signature).

You have already insinuated yourself into this thread in a manner not helpful to the OP, so please take the opportunity from this point forward in this thread to provide constructive assistance to the OP or start a thread of your own to express your opinions.  Opinions are fine.  Gripes and comments that disparage developers/programmers/purveyors of operating systems are not.

Further, please DO NOT attempt to instruct other users what they may or may not link in their posts.  That is not your place on the Forums, and particularly not your place in another user's thread.

If you do not like what Canonical has done (which is certainly NOT like Microsoft as it is not forcing anything and is not just of benefit to sysadmins) with an OS that still does not force you to upgrade or even to install well-advised updates, you are free to use another distro.  You won't hurt our feelings.

---

### Post by QIII on 2022-09-26
While phased updates as currently configured are somewhat poorly explained in the "held back" message, I am not sure if the infrastructure of apt would allow for a by-package explanation of the reason for being held back beyond the depends messages.  Conceptually, I think phased updates are a brilliant idea.

However, I do dislike unexplained, vague and inscrutable messages -- my practice was to provide concise and understandable messages when I was still working -- but as I say I'm not sure if the system would allow for explanations.  I do think it would be prudent for the developers to find a way to do it.

---

### Post by georgesgiralt on 2022-09-27
Hi !
I did not know I opened a can of worms here. Apologies.
But, I spent 40 years working as an IT sysadmin in Unix/Linux environments. I retired a couple of years ago and, even if I'm not as sharp as I was, I can't understand what is the rationale behind "phased updates". 
Either you have new versions of software available and you post them and install them or you don't and then you wait until they are. Now there is another state. "I've got them ready and packed, but you are not mature enough for them now. Wait a couple of weeks or month and you'll be ready. But I show them to you to tease and make you wonder why they're not installed right away".... 
I do not know if it is from old age but I less and less understand this world and the direction it is aimed at. I think we lack some sort of thinking at a higher level. 
Anyway, thank you all for the very informative answers you gave.
Have a nice and bright day !

---

### Post by ian-weisser on 2022-09-27
> **georgesgiralt said:**
> the rationale behind "phased updates". 

It's based upon the real-world experience that some upgrades have problems despite testing and/or have unanticipated consequences when released into the wild. It's happened before, and it was terrible to try and clean up.

Phased Updates simply offers Ubuntu the opportunity to cancel an upgrade rollout if early-adopters report major problems. The idea is that 10% of users affected is better than 90% of users affected. It's another layer of protection. And it's simple users to opt-out and resume the older apt behavior if they really need to.

```

apt -o APT::Get::Always-Include-Phased-Updates=true upgrade

```

(It can also be added to /etc/apt/apt.conf.d/ for regular use, though I recommend against that for folks who lack a good reason)

The apt developers received little feedback on Phased Updates from 21.04 or 21.10, so it's understandable if they expected most of the kinks had been worked out. Right now, the big loud bug they are working is getting dependencies to all phase together -- that's a key cause of long lists of "kept back" packages.

There's a running theme here of "not enough volunteers jumping in to help test," but that seems outside the scope of this thread. We work with what we have.

---

### Post by Paddy Landau on 2022-09-27
> **halogen2 said:**
> … create a file…
Thank you. This makes it clear! I tested this, and it works well in both apt and Synaptic, but (as expected) in neither Software Updater nor Ubuntu Software.

Interestingly, Gnome Software Store ignores phased updates, and does update everything, albeit with the irritating assumption that *all* apt updates require restarting!
> **ne29914 said:**
> Your own (#15 in this thread).
I fully agree. [The post is]("https://ubuntuforums.org/showthread.php?t=2479483&p=14113643#post14113643") both concise and perfectly understandable.

---

### Post by &amp;KyT$0P# on 2022-09-27
> **Paddy Landau said:**
> Thank you. This makes it clear! I tested this, and it works well in both apt and Synaptic, but (as expected) in neither Software Updater 

It not working in Software Updater [is a bug]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1979238") (note comment #2 in that bug report).

---

### Post by Paddy Landau on 2022-09-27
> **halogen2 said:**
> It not working in Software Updater [is a bug]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1979238") (note comment #2 in that bug report).
I see that the bug report is about using the machine ID rather than the Always-Include-Phased-Updates option. Is that really the same thing? (I don't know enough about apt to make an informed decision, sorry.)

---

### Post by &amp;KyT$0P# on 2022-09-27
> **Paddy Landau said:**
> I see that the bug report is about using the machine ID rather than the Always-Include-Phased-Updates option. Is that really the same thing? (I don't know enough about apt to make an informed decision, sorry.)

I interpret that comment #2 as saying the plan to fix that bug is to remove Software Updater's phased updates implementation, so that it just uses apt's implementation for phased updates.  Which would cover all 3 of apt's options for handling phased updates.  So if I understood correctly, yes it would be the same.

---

### Post by Paddy Landau on 2022-09-27
> **halogen2 said:**
> I interpret that comment #2 as saying the plan to fix that bug is to remove Software Updater's phased updates implementation, so that it just uses apt's implementation for phased updates.  Which would cover all 3 of apt's options for handling phased updates.  So if I understood correctly, yes it would be the same.
Thanks. I've upvoted it now.

---


---
title: "Question on Firefox 2 and Dapper"
date: 2007-01-05
forum: General Help
---

### Post by chrispche on 2007-01-05
I want to update to Firefox 2 although in Synaptic Manager the only version is 1.5 something. If I want to update to version 2. Would it be crafty and wise to change the sources.list file to update to edgy rather than dapper and then I should I assume get the option to update to Firefox version 2. From what I gather edgy's repos have this option. So I guess what I'm asking is can I fool dapper into getting edgy repos and get the firefox upgrade through apt-get firefox? Obviously I would have to update the repos once I changed the sources.list file.

Or is this all highly dangerous???

---

### Post by energiya on 2007-01-05
In my opinion, that would somehow be a messy upgrade method... I wouldn't recomand it. I think you should try Swiftfox. Get it from [here]("http://getswiftfox.com/").
> Swiftfox is an optimized build of Mozilla Firefox. Swiftfox has builds for both AMD and Intel processors. The 2.0.0.1 release is based on Firefox 2.0.0.1.
You can then use it as your default browser. I have Edgy with Firefox 2 and still use Swiftfox, becouse it appears to be faster.

---

### Post by speedwell68 on 2007-01-05
I'm using Edgy and the repos for edgy have FF 2.0, yet the Feisty repos have FF 2.0.0.1 which is a critical security update.  All I did was this:  sudo gedit /etc/apt/sources.list and change all the references to edgy to feisty, then reload the sources in Synaptic, do the upgrade then change the file back again.  Never used dapper so don't know if it'll work or not, but don't see why not.

---

### Post by madmetal on 2007-01-05
take a look how to upgrade to firefox 2.0.0.1 in dapper

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by madmetal on 2007-01-05
> **speedwell68 said:**
> I'm using Edgy and the repos for edgy have FF 2.0, yet the Feisty repos have FF 2.0.0.1 which is a critical security update.  All I did was this:  sudo gedit /etc/apt/sources.list and change all the references to edgy to feisty, then reload the sources in Synaptic, do the upgrade then change the file back again.  Never used dapper so don't know if it'll work or not, but don't see why not.

mixing up repos imho is a bit risky and not recommended..

---

### Post by chrispche on 2007-01-05
Will the Dapper repos eventually have the latest version of Firefox out of interest?

---

### Post by madmetal on 2007-01-05
i think not, but with this script you can have the latest firefox at your dapper pc.

---

### Post by chrispche on 2007-01-05
Ok I'll give the script a go. But how advisable is it to keep up to date with the latest Ubuntu Distros for this sort of thing. I heard Dapper is the most stable thats why I choose it.

Also I think I'll give that Swiftfox a go. Curious.

---

### Post by Efwis on 2007-01-05
> **chrispche said:**
> Will the Dapper repos eventually have the latest version of Firefox out of interest?

no the repos won't have FF2 available. this is because the Ubuntu Devs have integrated FF with Gnome.

---


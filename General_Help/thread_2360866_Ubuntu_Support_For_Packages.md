---
title: "Ubuntu Support For Packages"
date: 2017-05-09
forum: General Help
---

### Post by anspectrum on 2017-05-09
Hello,

I know that Ubuntu LTS releases are supported for 5 years and regular releases for 9 months as mentioned [here]("https://www.ubuntu.com/info/release-end-of-life"). Now that is as far as development of apps is concerned. I was wondering if anyone has information as to the availability of packages in repositories, that for how long will they remain available. 

My reason for asking is that I am using Ubuntu 12.04 and not upgrading because certain third party packages are only compatible with 12.04. Please have a look at following output

```
XXX@Ubuntu:~$ ubuntu-support-status
Support status summary of 'OS':

You have 49 packages (2.4%) supported until October 2013 (18m)
You have 1 packages (0.0%) supported until May 2022 (5y)
You have 5 packages (0.2%) supported until November 2018 (18m)
You have 1709 packages (85.2%) supported until April 2017 (5y)

You have 170 packages (8.5%) that can not/no-longer be downloaded
You have 73 packages (3.6%) that are unsupported


```

So lets say if I intend to install ( or maintain) 12.04 for another 4-5 years, will official repositories be available?

---

### Post by howefield on 2017-05-09
> **anspectrum said:**
> So lets say if I intend to install ( or maintain) 12.04 for another 4-5 years, will official repositories be available?

The 12.04 repositories will be archived at some point fairly soon and be rendered unavailable under your present sources.list file. You would be able to change the sources.list to point to the new location and as I understand still use the repositories but with zero security updates it is probably a very bad idea to continue to use 12.04 but you are obviously aware of that.

There must be another way.

---

### Post by ian-weisser on 2017-05-09
No, the official repositories won't be available.
When a release reaches the end of support, the repositories are closed to general access.

There are several ways around the closure, but the workarounds are usually not worthwhile - a system running an EOL release of Ubuntu should NOT be connected to the internet.
EOL releases are vulnerable to known, published exploits now, and won't be fixed.

---

### Post by anspectrum on 2017-05-09
@howefield:

Thanks for the prompt reply and definitely it is helpful.

As far as security updates are concerned, this is my personal laptop and as such I don't have any secret info in there. As a matter of fact I've disabled automatic updates since long and I'm quite satisfied with what I've got.

However, I would like further suggestion on this (security) aspect from your side before I mark this thread as solved.

@ian-weisser:

Packages are available in repositories till date as I can see all of them in Ubuntu Software Center

---

### Post by howefield on 2017-05-09
> **anspectrum said:**
> However, I would like further suggestion on this (security) aspect from your side before I mark this thread as solved.

Not sure what you mean by that ?

As it stands there is no security with 12.04. The packages will not receive any updates whatsoever. There is an option to pay for [extended support]("https://insights.ubuntu.com/2017/03/14/introducing-ubuntu-12-04-esm-extended-security-maintenance/") but for a "home" machine it may well be too pricey to consider.

---

### Post by anspectrum on 2017-05-09
All right. I think I would stick with 12.04 for foreseeable future and meanwhile try to make my intended packages work in 16.04 using VMs.

As always, thank you for all the support and good work.

---


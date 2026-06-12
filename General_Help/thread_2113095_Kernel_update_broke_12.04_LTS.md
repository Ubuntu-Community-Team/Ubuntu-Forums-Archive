---
title: "Kernel update broke 12.04 LTS"
date: 2013-02-06
forum: General Help
---

### Post by Deer Hunter on 2013-02-06
Hello all,

On Saturday I fired up my laptop that runs Ubuntu 12.04 LTS and checked the updates, and it said among other things that there was a kernel update. So I updated, and had to restart again, no problem; but now, I can't log in. I just get a black screen with a little box saying
> Failed to load session "ubuntu"

and there's a little "Log Out" button there, which brings me to the login screen. I can't log in either into my own profile or into the guest login.

So what I want to know is, what happened and how can I fix it? I didn't change the update settings to get more recent, more unstable stuff. Any help is appreciated.

---

### Post by Deer Hunter on 2013-02-06
If it makes any difference, I'm running the 64-bit version. Any ideas, anyone?

---

### Post by ibjsb4 on 2013-02-06
At boot (login) click on the Ubuntu doughnut and try to log into Ubuntu 2D.  That may at least get you something to work with.

---

### Post by landersohn on 2013-02-06
what kernel version is broke?
I just installed 3.5.0-23.35, works peachy.
can you select one of your previous kernels in the grub screen and login?

---

### Post by Deer Hunter on 2013-02-06
Sorry to say, I can't implement either suggestion.

I took off Unity 2D, so that's not there.

I'm not sure which kernel it was, except that it was in the 3.5 line; I didn't pay attention because I wasn't anticipating it causing a problem.

My machine doesn't show a grub screen when I boot up.

I do have an old 10.04 disc around, maybe I can live boot with that and do something? Is that possible?

---

### Post by Butthead on 2013-02-07
> **landersohn said:**
> what kernel version is broke?
I just installed 3.5.0-23.35, works peachy.
can you select one of your previous kernels in the grub screen and login?

Hmm, my stock last Kubuntu 12.04 kernel after the last upgrade session is listed as 3.2.0-37-generic. :confused:

---

### Post by varunendra on 2013-02-07
> **Deer Hunter said:**
> My machine doesn't show a grub screen when I boot up.
When Ubuntu starts loading, press and hold 'Shift' key.

This should bring up the Grub menu from where you can try to boot with either

* the older kernel (3rd option - "older versions.."), or

* with the current one in "recovery mode" (2nd option in the menu).

Can you get into any of these successfully?

---

### Post by DuckHook on 2013-02-07
> **Butthead said:**
> Hmm, my stock last Kubuntu 12.04 kernel after the last upgrade session is listed as 3.2.0-37-generic. 

...which is entirely appropriate. 12.04 is on the 3.2.x series. @landersohn is probably running 12.10 unless he has dist-upgraded older versions which is not recommended, as the 12.04 apps in the repositories were built for the 3.2.x series kernels.

---

### Post by DuckHook on 2013-02-07
> **varunendra said:**
> When Ubuntu starts loading, press and hold 'Shift' key.

On some systems, you need to press <Esc>. Don't know why, but if <Shift> doesn't work, try <Esc>.

---

### Post by deadflowr on 2013-02-08
> **Butthead said:**
> Hmm, my stock last Kubuntu 12.04 kernel after the last upgrade session is listed as 3.2.0-37-generic. :confused:

the 3.5 kernel is the lts-quantal kernel, which is available in the precise repos, hence lts.

---

### Post by Deer Hunter on 2013-02-09
Hello, thanks for your replies.

First off, my bad, I was way out to lunch on the kernel. By holding 'shift' like was mentioned above, I got GRUB and could see that it was actually 3.2.0-37-generic which was at fault. I'm typing this from the Ubuntu machine, booted into the 3.2.0-36-generic kernel. Recovery mode on 3.2.0-37-generic didn't seem to help much, although maybe I don't know enough to understand what I could have done there to fix things.

Thanks for the help so far!

---

### Post by Deer Hunter on 2013-02-09
So, I guess now my question is, how can I either repair the 3.2.0-37-generic kernel so it works, or remove it so that I can just boot into the 3.2.0-36-generic kernel and operate on that?

---

### Post by DuckHook on 2013-02-09
> **Deer Hunter said:**
> So, I guess now my question is, how can I either repair the 3.2.0-37-generic kernel so it works, or remove it so that I can just boot into the 3.2.0-36-generic kernel and operate on that?

This is up to you. If you want to learn about Linux and this is not a production machine, then there is no better way to learn than wrestling with a balky update or install. If this is a production machine, then my recommendation is to not tinker with it but keep it working first. If that is your desire as well, then you need to pin the kernel so that it bypasses future updates. Instructions for pinning a kernel is [here]("https://help.ubuntu.com/community/PinningHowto").

<edit>
Perhaps a more detailed and focused set of instructions is [this]("http://ubuntuforums.org/showthread.php?t=2073529") one. Had to google it to get it again, although I remembered it as excellent guidance. I used it to pin a kernel for an ancient laptop that no longer runs on the modern kernels. Worked very well for me just following the exact steps in the post.
</edit>

<further edit>
Further thoughts:

If you don't regularly back up your important data, this is the computing gods' way of giving you fair warning to do so. Now that you have a working system again, safeguard you data first. Any problems or issues you encounter henceforth then becomes nothing more than an irritation. If you neglect backups, the next time, nobody may be able to help you, in which case, kiss goodbye to your irreplaceable photos, emails, etc.

If you want to chase down the problem with the update, then require far more system info. Read [this]("http://ubuntuforums.org/showthread.php?t=1422475") sticky at the top of the forum page.
</edit>

---

### Post by Deer Hunter on 2013-02-23
Last update: I pinned the kernel, and it booted up fine once again. Thanks DuckHook for your help! My laptop isn't a production machine, but I just didn't want to try to fight something like that.

Anyway, I'm now marking this thread "Solved."

---


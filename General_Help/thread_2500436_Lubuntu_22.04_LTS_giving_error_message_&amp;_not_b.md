---
title: "Lubuntu 22.04 LTS giving error message &amp; not booting up"
date: 2024-09-01
forum: General Help
---

### Post by AbleTassie on 2024-09-01
I just booted up Lubuntu 22.04 LTS an hour or two ago and now it will not boot up. I get an error message as the PC is booting up that appears in the upper left corner of the screen that says (exactly as it appears below):

Verifying shim SBAT data failed: Security Policy Violation
Something has gone seriously wrong: SBAT self-check failed: Security Policy Viol
ation

QUESTION: Does anybody have any idea what's wrong and what I should do?

Thank you,

A.

P.S. I am dual booting Windows 11 and I am using the Windows side to make this post

---

### Post by Rubi1200 on 2024-09-02
One of the forum members posted about this just a few hours ago:
[https://ubuntuforums.org/showthread.php?t=2500420](https://ubuntuforums.org/showthread.php?t=2500420)

Hopefully you can find a solution there.

---

### Post by guiverc on 2024-09-02
Result of a *badly done* Microsoft SBAT change.

Refer [https://arstechnica.com/security/2024/08/a-patch-microsoft-spent-2-years-preparing-is-making-a-mess-for-some-linux-users/](https://arstechnica.com/security/2024/08/a-patch-microsoft-spent-2-years-preparing-is-making-a-mess-for-some-linux-users/)

Or i'll provide a quote from a recent *Ubuntu Weekly Newsletter *issue

> 
**“Something has gone seriously wrong,” dual-boot systems warn after Microsoft update**

 Dan Goodin reports on a windows fix to a two year old vulnerability  that had some unforeseen issues. With details of the problem, and  Microsoft’s fix; a fix that didn’t work for many people & thus left  systems that failed to boot. We’re walked through this story, and the  consequences, before being given steps for a workaround with mention of  some of the problems in the secure-boot approach.

[https://arstechnica.com/security/2024/08/a-patch-microsoft-spent-2-years-preparing-is-making-a-mess-for-some-linux-users/](https://arstechnica.com/security/2024/08/a-patch-microsoft-spent-2-years-preparing-is-making-a-mess-for-some-linux-users/)



[LIST]
[*]Microsoft’s latest security update has ruined dual-boot Windows and Linux PCs - [https://www.theverge.com/2024/8/21/24225108/microsoft-security-update-windows-linux-dual-boot-errors](https://www.theverge.com/2024/8/21/24225108/microsoft-security-update-windows-linux-dual-boot-errors) 
[*]SBAT self-check failed: Mitigating the impact of shim 15.7 revocation on the Ubuntu boot process for devices running Windows - [https://discourse.ubuntu.com/t/sbat-self-check-failed-mitigating-the-impact-of-shim-15-7-revocation-on-the-ubuntu-boot-process-for-devices-running-windows/47378](https://discourse.ubuntu.com/t/sbat-self-check-failed-mitigating-the-impact-of-shim-15-7-revocation-on-the-ubuntu-boot-process-for-devices-running-windows/47378) 
[*]Ubuntu SBAT reset media [https://github.com/canonical/sbat-reset-media](https://github.com/canonical/sbat-reset-media) 
[/LIST]



Quote from

- [https://ubuntuforums.org/showthread.php?t=2500232](https://ubuntuforums.org/showthread.php?t=2500232)
- [URL="https://discourse.ubuntu.com/t/ubuntu-weekly-newsletter-issue-854/47301/"]https://discourse.ubuntu.com/t/ubuntu-weekly-newsletter-issue-854/47301/

[/URL]

---

### Post by AbleTassie on 2024-09-02
Thank you Rubi1200 and guiverc,

I use the Lubuntu side by default for almost everything. But I use the Microsoft Windows side sometimes for things that I can't (or don't know how to) use the Lubuntu side for. I will report back if/when I find a solution.

Able

---

### Post by AbleTassie on 2024-09-02
I (apparently) solved the problem. I used the method described on this Microsoft webpage at 
[URL="https://learn.microsoft.com/en-us/windows/release-health/status-windows-11-23h2#3377msgdesc"]https://learn.microsoft.com/en-us/windows/release-health/status-windows-11-23h2#3377msgdesc

[/URL] [SIZE=2]**But I just want to double-check something:** I have one question: In the instructions at the link above Under Scenario 2, step c) it says:[/SIZE]
 
 [I][SIZE=2]"c) Verify SBAT Revocations:[/SIZE]

     [SIZE=2]In the terminal, run the below command:[/SIZE]
 
 [SIZE=2]mokutil --list-sbat-revocations[/SIZE]
 
     [SIZE=2]Ensure the list shows _**no**_ revocations."[/SIZE][/I]
 
 [SIZE=2]But, when I run that terminal command I get, a revocation, specifically, &#8220;sbat,1,2021030218&#8221; is listed as a revocation. Specifically, this is copied and pasted from the Terminal screen:[/SIZE]
 
  [SIZE=2]able@able-x556uq:~$ mokutil --list-sbat-revocations [/SIZE] 
 [SIZE=2]sbat,1,2021030218 [/SIZE] 
  [SIZE=4][SIZE=2]able@able-x556uq:~[/SIZE][/SIZE]
 
  [SIZE=2]QUESTION(S): But I think this is what I want, isn&#8217;t it? 
In other words I want  sbat,1,2021030218 to be revoked, don&#8217;t I?[/SIZE]
 
  [SIZE=2]Thank you again,[/SIZE]
 
  [SIZE=2]Able[/SIZE]

---

### Post by ActionParsnip on 2024-09-03
[https://www.omgubuntu.co.uk/2024/08/windows-update-breaking-linux-dualboot-fix](https://www.omgubuntu.co.uk/2024/08/windows-update-breaking-linux-dualboot-fix)

---

### Post by yancek on 2024-09-03
Do you have Secure Boot enabled in your BIOS?  Have you tried booting it with Secure Boot disabled?  Not sure if this will help.  If Secure Boot solves this boot problem but you want it on you will need to find another solution such as the one at the link posed above.

If you are going to continue dual booting Linux and windows you need to be aware that some windows updates will do things like this and will also turn hibernation back on if it turned off by the user (which will prevent access to windows data partitions from Linux) and will sometimes change the BIOS boot order to put windows first.

---

### Post by AbleTassie on 2024-09-07
Thanks ActionParsnip and Yancek,

I had to disable and then re-enable Secure Boot as described above at [https://www.omgubuntu.co.uk/2024/08/...x-dualboot-fix]("https://www.omgubuntu.co.uk/2024/08/windows-update-breaking-linux-dualboot-fix") to get to a solution. It is working. I am able to use Lubuntu, in fact am using it right now to make this post. And I think that I want [SIZE=2]sbat,1,2021030218 to be revoked. So I am going to mark this thread as SOLVED.

If anybody else had any comments they will be welcomed.

Thanks,

A.
[/SIZE]

---


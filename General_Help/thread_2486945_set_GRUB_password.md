---
title: "set GRUB password"
date: 2023-05-17
forum: General Help
---

### Post by thuan250 on 2023-05-17
Hi all,

I'm trying to implement this STIG for our AWS EC2 Ubuntu 18.04, but it failed during startup.
[https://www.stigviewer.com/stig/canonical_ubuntu_18.04_lts/2022-12-06/finding/V-219147](https://www.stigviewer.com/stig/canonical_ubuntu_18.04_lts/2022-12-06/finding/V-219147)
It'll prompt for username and password.
But there is no way for me to input the credentials.
As a result, the EC2 health check failed and we can't log into it.
Does anybody in here have try this?

Thanks

---

### Post by MAFoElffen on 2023-05-17
Yes...
> 
[h=1]Warnings & Cautions[/h] 
[LIST]
[*]Errors in creating a  password-protected GRUB 2 menu may result in an unbootable system. To  restore a system with broken passwords, access and edit the GRUB 2  configuration files using the LiveCD or another OS. 
[*]If password protection is enabled, only the designated superuser can edit a Grub 2 menu item by pressing "**e**" or access the GRUB 2 command line by pressing "**c**". 

[*]If  GRUB 2 is set up to boot automatically to a password-protected  menuentry the user has no option to back out of the password prompt to  select another menuentry. Holding the SHIFT key will not display the  menu in this case. The user must enter the correct username and  password. If unable, the configuration files will have to be edited via  the LiveCD or other means to fix the problem.  
[*]Users  experimenting with GRUB 2 passwords should keep at least one  non-protected menuentry and set the timeout to at least 1 second until  testing is complete. This will allow booting to correct problematic  settings.
[/LIST]

I used these instructions: [https://help.ubuntu.com/community/Grub2/Passwords](https://help.ubuntu.com/community/Grub2/Passwords)

---

### Post by thuan250 on 2023-05-18
Does it work for you?

Thanks

---

### Post by TheFu on 2023-05-18
18.04 standard support ends this month.  Best NOT to be installing it without paid commercial support.
Performing an upgrade to the next LTS, 20.04, will get harder in a few weeks as repos are removed and relocated.  Without the commercial support, no new patches for any issues will be available to 18.04 systems, which definitely violates STIGs.

---

### Post by thuan250 on 2023-05-18
We have commercial support.
The EC2 is inaccessible whenever the BIOS password is set.

---

### Post by MAFoElffen on 2023-05-18
I have used Grub2 encrypted passwords on KVM VM images and one metal. I have not used it on Cloud images. On metal, I felt it was a security risk, as the Grub2 passwords, even though encrypted, are stored in the clear, and can be read.

Since you are required to comply with the STIG, are proabably using AWS Task Orchestrator and Executor, using EC2 GovCloud, and since you have paid 24/7 support from Ubuntu Pro:
[https://ubuntu.com/blog/us-public-sector-regulatory-compliance-with-ubuntu-pro-and-aws-govcloud](https://ubuntu.com/blog/us-public-sector-regulatory-compliance-with-ubuntu-pro-and-aws-govcloud)

...You should be calling your Ubuntu Pro support Line, or AWS, and using your paid support to get help to get that to work for you.

If that is required by the STIG to be in place for AWS GovCloud for Winodws and Linux Images, then I'm sure they have it working somehow, and can help you with that.

---

### Post by TheFu on 2023-05-18
Google found this: [https://stackoverflow.com/questions/49870779/aws-ec2-linux-grub-with-password](https://stackoverflow.com/questions/49870779/aws-ec2-linux-grub-with-password)  Seems a less than ideal method, unless the point of the grub password is to prevent non-approved options from being entered by anyone, but allowing the default boot choice/options to happen without entering any password.

I haven't used EC2 in about 15 yrs.

---

### Post by thuan250 on 2023-05-19
@TheFu

I read this post in the past and tried it, but no luck.
The latest kernel of Ubuntu 18.04 already has the --unrestricted parameter in menu entries.
Thanks for the link though

This STIG is not ideal for cloud environment, security engineers should revise this STIG or remove it.

---


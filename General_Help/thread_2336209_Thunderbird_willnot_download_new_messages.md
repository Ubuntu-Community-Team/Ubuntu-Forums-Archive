---
title: "Thunderbird willnot download new messages"
date: 2016-09-05
forum: General Help
---

### Post by jlh68 on 2016-09-05
I tried the Mozilla - TB forum, and I get no responses, as usual.  So I am asking the Ubuntu users to help.

I am using (or was when it worked) Thunderbird 45.2.0 for email.  When I click on get messages, the inbox whirling icon, just spins until I close TB.  No new emails are down loaded.  There are several other quirks with TB, but this is the most outstanding one.  TB is useless if one can not download new messages, or send out messages.  I have tried this on two different ISP's with the same lack of results.  One ISP in Charlotte, NC, and one here in Staunton, Va. so I don't feel that it is an ISP problem.

I have some saved emails that I don't want to loose or I would just uninstall TB, and then reinstall.  I did use Synaptic Package Manager to reinstall and that did not help.

Anyone have or had this problem and know what the cause is?  I would appreciate any help on this.  Like I said, I started on the Mozilla - Thunderbird forum and for 4 days, I have not had one response.

I am using my System76 laptop.

---

### Post by &amp;KyT$0P# on 2016-09-05
Do you have any affected accounts set up as IMAP?
If so, please set up those accounts - **only the IMAP accounts** - in a new, clean [profile]("http://kb.mozillazine.org/Profile"), and let us know whether you experience the same problem there.  This is probably the most straightforward way to check whether the issue is something local.

---

### Post by SuperFreak on 2016-09-05
Should be possible to back up your emails. Look under Account Settings/Server Settings and at the bottom it will show the location of the local directory. This is where your Inbox, Sent, Archive, etc emails are stored. Back up that folder and then remove Thunderbird and then try to reinstall Thunderbird and then make sure the old Folder with your emails replaces the new one.

---

### Post by &amp;KyT$0P# on 2016-09-05
> **SuperFreak said:**
> Back up that folder and then remove Thunderbird and then try to reinstall Thunderbird 
Unless we're going to be trying a different version or build of Thunderbird, uninstall/reinstall don't accomplish much as the user data is all stored in the profile.  I don't think we're there at this point. :)

---

### Post by jlh68 on 2016-09-05
I just updated my **Netbook** from Linux kernel 4.4.0.31 to 4.4.0.36.  Thunderbird was working before the upgrade, and now I have the same problem as I do with my **Laptop**.  As I remember back I think it was the Ubuntu upgrade that broke Thunderbird on my Laptop and now it has broken it on my Netbook also.

At this point I believe it is the Ubuntu/Linux kernel breaking Thunderbird.

Netbook is an AMD processor and the Laptop is an Intel processor.

---

### Post by autocrat on 2016-09-05
Is it possible that a setting within TB is preventing you from DLing new messages?

[https://support.mozilla.org/en-US/kb/cannot-receive-messages#w_did-your-ability-to-receive-mail-suddenly-stop-was-it-working-before](https://support.mozilla.org/en-US/kb/cannot-receive-messages#w_did-your-ability-to-receive-mail-suddenly-stop-was-it-working-before)

---

### Post by &amp;KyT$0P# on 2016-09-05
> **jlh68 said:**
> At this point I believe it is the Ubuntu/Linux kernel breaking Thunderbird.
Sounds extremely unlikely to me but if you think it could be the culprit it's not that hard to check ;)
Reboot your system, get into the GRUB menu (if you don't see it, press Shift or Esc after powering on and before the OS starts to boot) and select the latest kernel version you think was working. (You do still have it installed right?  If you're unsure, run [FONT=Courier New]dpkg-query -W | grep -P -i '^linux'[/FONT] to check if it's there)

Does Thunderbird work then?

---

### Post by jlh68 on 2016-09-05
On my Laptop I went back to 4.4.0.31 and the problem still exists. I would have thought that reverting to a kernel that Thunderbird worked with would at least get it to work with it again..

On this Netbook I am going to uninstall TB and then re-install and see what happens.

---

### Post by speartip on 2016-09-06
Uninstalling & Reinstalling Thunderbird will probably make no difference. It will still link to the same profile which might be corrupted. Try Setting up Thunderbird with a new profile. In your home folder you will have a hidden file called .thunderbird. Rename it to .thunderbird2. Open Thunderbird again. It should now be like a fresh install. Setup your profile again, and see if they now download. If not delete your new .thunderbird folder & rename .thunderbird2 back to .thunderbird, to get back to where you where.
 If your profile isn't the issue, these problems are normally caused by the email provider, not Thunderbird. What email provider do you use?

---

### Post by jlh68 on 2016-09-06
My email provider is Lumos.net.   Lumos is also my ISP provider.  This same problem existed when I was in Charlotte, NC on I think it was Time-Warner ISP.
I will try the profile change and let all know if it works or not.  It is strange that this problem is on two different computers.

---

### Post by speartip on 2016-09-06
Thunderbird IMO is a very stable reliable program. I would be surprised if it was the problem.
You could try setting up a gmail account, to see if that behaves properly in Thunderbird. If it does, at least then the issue points more toward Lumos & the way it is configured.

---

### Post by jlh68 on 2016-09-06
OK I finally got the solution to the problem.  From my ISP IT technician, he says that Mozilla Thunderbird update changed some of the account settings.  These settings did not reverse when going back to an earlier Linux kernel.  

Thanks Ubuntu Forum members for your support.  I am surprised that the Thunderbird Forum never answered my question or ever asked for more information.

That is why I like the Ubuntu Forum members as we all are trying to help each other get it to work

---

### Post by &amp;KyT$0P# on 2016-09-06
> **jlh68 said:**
> OK I finally got the solution to the problem.  From my ISP IT technician, he says that Mozilla Thunderbird update changed some of the account settings. 
Thank you for posting this and glad you have it working again. :KS

Which specifically account settings got changed and is it known why?

---

### Post by jlh68 on 2016-09-06
I spoke too soon.  I now can download messages now, but I can not open them.  It is stuck on one and will not move to and open any other messages.   Bummer.

---

### Post by &amp;KyT$0P# on 2016-09-06
Is that account set up as IMAP or POP?
Is this new problem occurring across all your accounts?  Do you have any accounts where this doesn't happen?

---

### Post by mc4man on 2016-09-06
wrong thread

---

### Post by jlh68 on 2016-09-16
It is IMAP and I am wondering if it should be POP?  Only thing is I use several different computers.  I need to figure out in on POP how to leave them on the server when I am not on my main computer.

The emails are definitively slow to load in IMAP.

---

### Post by &amp;KyT$0P# on 2016-09-16
> **jlh68 said:**
> It is IMAP 
Good, IMAP makes testing safer as there isn't the risk of email data loss going between profiles.

So please create a new Thunderbird [profile]("http://kb.mozillazine.org/Profile"), leave all the defaults and do not install any extensions.
Set up your email account as IMAP "from scratch".
Does the problem exist?

---


---
title: "Single User Multiple computers"
date: 2014-03-13
forum: General Help
---

### Post by william26 on 2014-03-13
Is there anything like the Windows Server ability to give authorities to different computers?
I'm sorry, I don't have the proper key words to ask what I'm looking for.

At my office I have a login to my computer.  This login will bring up my desktop, calendar, mail, ect.  I have the authority to do this on any computer in our company.  I can login and bring up my desktop.  My secretary has a login that only works on her computer.  She cannot walk into my office and login to bring up her desktop.

Is there anyway to setup this sort of configuration if we change from Windows to all Ubuntu?

Forgive me if this has already been asked.

---

### Post by lukeiamyourfather on 2014-03-13
Yes, this is possible with Ubuntu or even a mix of Ubuntu and Windows clients.

---

### Post by SeijiSensei on 2014-03-13
In fact, if you have an Active Directory installation, Linux can [authenticate users against the AD]("https://help.ubuntu.com/community/ActiveDirectoryHowto").

I would strongly argue against any wholesale conversion from Windows to Linux.  I'd start first with a couple of highly-savvy users and work with them on a project to test out Linux implementation.  This isn't a decision to take lightly, and there are many more important things to consider than single-sign-on.  Does your organization rely on applications that only run on Windows?  How about devices like printers and scanners? Support for the latter can be dicey.  How much are you willing to spend to retrain your employees?  How would switching to Linux affect your organization's interactions with other organizations?  If everyone you work with expects to get documents in .docx and .xlsx, that may be an important stumbling block right three.

---

### Post by whitesmith on 2014-03-13
+1 to SeijiSensei for his answer. Start with the first entry in my sig line.

---

### Post by william26 on 2014-03-13
Thank you I found [https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP) as is always the case AFTER you search for days and ask a question.
[COLOR=#000000]
[/COLOR]> This isn't a decision to take lightly, and there are many more important things to consider than single-sign-on.
Agreed!  I understand and appreciate your concerns about conversion from Windows.

Let me answer your questions ( all very good by the way ):
> Does your organization rely on applications that only run on Windows?
Rely is a strong word.  Are there any programs that we use that are written only for Windows, yes.  Are there alternatives.  Yes.  Have we contacted the vendors informing them of our future plans.  Yes.  Will they change.  History shows that they will not, until it bites them in the wallet.
> How about devices like printers and scanners? 
Solved.  Several years ago we switched to common printers and scanners to reduce waste, save money and ease help desk questions.  It's easier if you only have one or two printers to diagnose.  Do we have the crazy 3D printer or plotter out there in some of our testing labs that may not work.  Yes, we can handle the one or two cases and plan for new purchases if we have set a path on switching to another OS.
> How much are you willing to spend to retrain your employees?
In our testing, training employees to use Windows 8/8.1 was more painful than training for Ubuntu.  And now there's Windows 9 just over the horizon.
> How would switching to Linux affect your organization's interactions with other organizations?
Solved, our test group hasn't had any MAJOR problems with integration with other organizations.  Typically, the test group becomes smug and looks down upon Windows users.  We are still working on how to overcome that.
> If everyone you work with expects to get documents in .docx and .xlsx, that may be an important stumbling block right three.
Ubuntu core applications can export in those formats.  Again, smugness at having to do so is a problem.

We are only considering alternatives as scalability is becoming troublesome.  Handling the licensing of 60K devices is a huge concern.  Typically apps under the Windows model also requires additional licensing.  All of this adds up to a ridiculous price.  We feel that this is not something we cannot continue and are looking at alternatives.  I've been using linux for many years and Ubuntu since 2009, but only personally.  We are very serious about how any changes will impact the organization.

---

### Post by JKyleOKC on 2014-03-13
> **william26 said:**
> Is there anyway to setup this sort of configuration if we change from Windows to all Ubuntu?The simple answer is "yes" but if you are contemplating making such a change because of the impending EOL for Windows XP, I must agree with the other replies pointing out that doing it in a hurry is an **Extremely Bad Idea**.

It cannot be repeated too often that Linux (Ubuntu) is **NOT** Windows. The systems are as different as an airliner differs from a cross-country passenger train. Linux is based on principles that are even older, by almost 20 years, than Windows, but those principles are so drastically different that your people's knowledge of how to do their jobs using Windows will require months, not days, of intensive re-training.

One reply noted that exchange of documents with the rest of the world that's still using Microsoft's "docx" format will be seriously impacted. Many programs that run only on XP and cannot even be used on later versions of Windows will require replacement -- and such replacements often aren't available at any price.

Making a change such as this is definitely worth exploring, but needs extensive testing and allowance for the "hidden" costs of lost productivity during and immediately after the changeover. Almost 25 years ago, I oversaw a similar switch of production software in a manufacturing plant. Despite more than a year of preparation and extensive re-training for all users, the accounting software went **$11 million** out of balance in less than six months after the switch, and within 18 months that company had gone under. Be very, very cautious!!!

---

### Post by JKyleOKC on 2014-03-13
> **william26 said:**
> Solved, our test group hasn't had any MAJOR problems with integration with other organizations.  Typically, the test group becomes smug and looks down upon Windows users.  We are still working on how to overcome that.

...snip...

Ubuntu core applications can export in those formats.  Again, smugness at having to do so is a problem.

We are only considering alternatives as scalability is becoming troublesome.  Handling the licensing of 60K devices is a huge concern.  Typically apps under the Windows model also requires additional licensing.  All of this adds up to a ridiculous price.  We feel that this is not something we cannot continue and are looking at alternatives.  I've been using linux for many years and Ubuntu since 2009, but only personally.  We are very serious about how any changes will impact the organization.Looks as if you've done your homework quite well. My earlier response was being written before your reply appeared.

Smugness will continue to be a problem until the conversion is complete. It will become less of a problem as more people make the switch, but of course you can expect a few holdouts who simply claim to be unable to deal with the "new" software. In such cases I tend to tell people that if they cannot learn how to do their jobs, their replacement will be able to...

Exporting from office applications may be more of a problem than you think, though. All the programs that I have used actually do the export in RTF format, with the result that complex layout and formatting data can get lost. I've even experienced a few cases in which such translation makes it impossible for older versions of Word to work with a translated document. I've solved them each time as they arose, but my productivity plummets each time that happens.

---


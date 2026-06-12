---
title: "Bad Bot, Go Away, Really Ubuntu Team?"
date: 2021-11-09
forum: General Help
---

### Post by Nattereri on 2021-11-09
How is one supposed to log into launchpad to report a bug with the launchpad website when you can't log in to launchpad? I must say I thought I left this kind of stuff behind when I switched from MS. I keep getting an error that says Bad Bot, Go Away. How am I supposed to get back in? Even better, who am I supposed to report this to so it can be fixed? Or am I just supposed to move on to another distro?

---

### Post by grahammechanical on 2021-11-09
This is what one Ubuntu developer said way back in 2015 in a bug report on this issue:

> I've tested all reported browsers, and they work for me. Please note  that the error you are getting with the "Bad bot" means that the form  submission process received more fields that those visible to the end  user, thus indicating that the form was likely submitted by an automatic  script that is filling more fields than what it should.

I have no problem logging in to Launchpad. But then again I do not allow the browser to save any passwords. From reading the bug report the problem occurs when a username is an email address and the application that saves the username and password puts the email address username in the email field and not the username field. 

> FYI — To "fix" this obnoxious issue in order to use KeeFox, you need to tell it to use the "email" field instead of "openid.usernamesecret"  for the username.  You can do this by editing the entry in KeePass,  going to the KeeFox tab, form fields, and edit the "{USERNAME}" form  field, changing the name to "email" (the default is blank).


[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1413665](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1413665)

Regards

---

### Post by guiverc on 2021-11-09
It's not a Canonical issue directly; but a bug (regression) in the firefox snap packaged by Mozilla.

A newer bug (re-filed) bug to that @[[COLOR=#000000]grahammechanical [/COLOR]]("https://ubuntuforums.org/member.php?u=1087323")mentioned is

[https://bugs.launchpad.net/canonical-identity-provider/+bug/1950073](https://bugs.launchpad.net/canonical-identity-provider/+bug/1950073)

Yes it's a known issue, and will be resolved as quickly as possible.

(I experienced it about six times yesterday using `ubuntu-bug` (3 QA-tests), but it doesn't always occur as one *daily* booted & reported the first time without issue, alas not the boxes second).

---

### Post by ActionParsnip on 2021-11-09
Try
```

ubuntu-bug packagename

```
This should kick off the process for you

---

### Post by guiverc on 2021-11-09
@ActionParsnip

the collection of bug report data via `ubuntu-bug` (*what is within Canonical/Ubuntu control*) works, if you're using the `firefox` snap & have the latest from Mozilla; the Mozilla snap can fail to login due to [issue]("https://bugzilla.mozilla.org/show_bug.cgi?id=1739992") and the launchpad site rejects you as a bot as bad data is passed to launchpad from firefox.  (*mozilla bug report was found in my last comment** in bug report*)

The mozilla bug report (*this comment*) has a workaround, but you'll find work-arounds in the bug report (eg. by [Leó Kolbeinsson (leok]("https://launchpad.net/~leok"))) in my prior comment, alas they'll only work once before needing to be re-done.

---

### Post by grahammechanical on 2021-11-09
I am using 20.04 with the Firefox snap installed and I cannot replicate this issue. I do not use a password manager or allow Firefox to save usernames and passwords.

From the new bug report:

> A  workaround you can also try is removing your password manager record  for Launchpad, which should clear the incorrectly-filled field, and then  try logging in again to create a new record (please write your password  down before removing the record!).

 Another option is to go into the password manager and clear any auto-filled values for openid.usernamesecret (which is the bot detection field which should be left blank).




Regards

---

### Post by mastablasta on 2021-11-10
> **guiverc said:**
> 

Yes it's a known issue, and will be resolved as quickly as possible.


workaround would be to use different browser (e.g. chromium, brave, opera...). 

i have 2 browsers installed plus a text only one just in case :)

---

### Post by Nattereri on 2021-11-10
Thanks for all of your replies. I tried clearing the saved password and that's when I realized it was user confusion. Some months ago I changed the email address on my Launchpad account and Ubuntu One was logged in with the old email.

---

### Post by monkeybrain20122 on 2021-11-10
> **mastablasta said:**
> workaround would be to use different browser (e.g. chromium, brave, opera...). 

i have 2 browsers installed plus a text only one just in case :)

Or just uninstall the Firefox snap and install either the .deb (it is still in 21.10 repo since the flavours haven't switched to FF snap)  or  download the distro agnostic tarball from Mozilla and just run it locally. There is no reason why one should have to put up with buggy defaults when there are other options.

---

### Post by guiverc on 2021-11-10
The issue is noticed most on *daily* images used in QA-testing, as they have the latest software AND don't have anything but a default setup.

I've not noticed any issues on my primary/configured boxes; but I file few bugs there, but I can do things on those *configured* boxes that just get bot-go-away messages when using a *daily* image in *live* mode.

I tried removing the `firefox` snap on a Ubuntu *jammy canary *live ISO, then adding the`firefox` *deb* package - and still had (bad bot) issues yesterday... but I didn't explore why (*despite it contradicting what I felt I understood the issue as being*) as the bug report would have been a *duplicate* I'm 99.9999% sure.

I've got a new (upgraded with newer canary installer build) *daily* written to thumb-drive so I'll try again today...  Hopefully today I won't need to file bug reports so won't hit the issue again :)  *and fingers crossed.*

---


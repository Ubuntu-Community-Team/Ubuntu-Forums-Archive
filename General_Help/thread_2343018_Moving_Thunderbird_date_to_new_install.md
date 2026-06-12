---
title: "Moving Thunderbird date to new install"
date: 2016-11-12
forum: General Help
---

### Post by Qualtrough on 2016-11-12
I have a PC set up with 12.04 and have been using that for a long time. Due to upgrade issues I purchased another PC and installed 16.04 on that. What I want to do is move my Thunderbird data (inbox, send mail, etc.) to the new machine. I have done some research and it seems there are a number of ways to do this. What I attempted was to set up a new Thunderbird profile, and then delete all the content, and then paste all the content from the old profile into the new one. However, I can't get this to work. All that happens when I fire Thunderbird up is that it starts to download all the mail on my server, no sent mail or anything else appears. If anyone can advise me or point me to clear step by step instructions on how to do this I would be grateful. I did this some time ago and I recall it being pretty easy, but so far I have spent the better part of today fiddling with this.

---

### Post by speartip on 2016-11-12
As long as the version of Thunderbird on your 12.04 & 16.04 installs are the same, which they should be if both installs are upto date, it should simply be a case of copying the .thunderbird folder from your home folder in 12.04, to your home folder in 16.04, after deleting the .thunderbird folder in 16.04. I have done this numerous times without issue.

---

### Post by gifford on 2016-11-12
I agree with speartip. Not always the suggested way of doing it but moving the folder does work. I also have not had any issues in doing so. The folder is the one with the .default extension, usually it has numerous letters like ztszrtq7.default

---

### Post by Qualtrough on 2016-11-12
Thanks both of you! I know I have done this before and it worked, not sure what issue I am having. I will check everything again, re-try, and let you know!

---

### Post by oldfred on 2016-11-12
I have regularly moved, copied & copied back my profile from days of XP and just about every Ubuntu install since 2006.

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by Qualtrough on 2016-11-12
OK. I see that I was copying the wrong file! Don't ask :) Anyhoo, I just did the following:

1. Copied the correct default file from the old installation. 
2. Opened Thunderbird in my new installation and then shut it down. 
3. Using the file manager I located the .thunderbird file
4. I opened the xxxx.default file, deleted the contents
5. I then pasted the contents in that from my old xxx.default file.
6. I fired up Thunderbird and all three of my email accounts were there along with all the inbox and outbox contents, archives, etc.

Great, but...

When I send test mails to the different accounts they send successfully, but when I check mail I don't see them! "No new mail to download"

I have looked at the server settings for each account and they look identical to the previous ones in the old computer.

Now I just found that sending an email from my cell phone works, i.e. it is received in one of my email accounts.

So here is my question:

Why would I be unable to send and received message between my accounts but be able to received emails from the same accounts but from my cell phone?

Update:

It looks like I can receive messages on all accounts OK, but I cannot send, even though I get a 'Message Successfully Sent' message each time I send and so far none of the message I sent have bounced back.

Update 2:

I can send messages to all my accounts via my cell phone, received with no problem.

A moment ago I sent a message from my old computer to my three accounts, this has not shown up yet.

I just checked my SMTP OUT Server settings against the providers specs and everything looks OK.

---

### Post by Qualtrough on 2016-11-12
Anyone? It now looks like I can send and receive via all three accounts OK, but I cannot send messages from one account to the other. I am sure I was able to do that previously.

Since issue seems to be unrelated to the installation (I have the same issue with the old computer) I will close this and ask about this in a new thread. Thanks everyone for your help!

UPDATE: Turns out there was an issue with my provider, and according to their recorded message they resolved it five minutes ago. I just checked and I can now receive messages sent to myself on all three accounts.

---

### Post by oldfred on 2016-11-13
Glad you got it resolved.

I rarely have issues, but my wife has to occasionally re-sign on to connect to Comcast.

---


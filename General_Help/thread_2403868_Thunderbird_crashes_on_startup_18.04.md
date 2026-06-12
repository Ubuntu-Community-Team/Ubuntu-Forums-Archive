---
title: "Thunderbird crashes on startup 18.04"
date: 2018-10-17
forum: General Help
---

### Post by monkeybrain2 on 2018-10-17
Hi all,
as the title says my thunderbird crashes on start. I am using Ubuntu 18.04.
When I start thunderbird in the terminal I get the following output
>  
(thunderbird:15704): Gtk-WARNING **: 11:37:20.588: Theme parsing error: <data>:1:34: Expected ')' in color definition

(thunderbird:15704): Gtk-WARNING **: 11:37:20.588: Theme parsing error: <data>:1:77: Expected ')' in color definition
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
ExceptionHandler::GenerateDump cloned child 15750
ExceptionHandler::SendContinueSignalToChild sent continue signal to child
ExceptionHandler::WaitForContinueSignal waiting for continue signal...

I already tried to re-install thunderbird, but doesn't change anything.
I also tried to google the error messages, but with no success.
thanks for any help!

---

### Post by howefield on 2018-10-17
Are you using the default Thunderbird/Desktop theme or have you installed a different one?

---

### Post by monkeybrain2 on 2018-10-17
I use the default theme

---

### Post by pqwoerituytrueiwoq on 2018-10-17
try launching with
[FONT=courier new]thunderbird --safe-mode[/FONT]
You can make a new profile if that does not work
[FONT=courier new]thunderbird --ProfileManager[/FONT]

---

### Post by monkeybrain2 on 2018-10-18
with >  thunderbird --safe-mode 
I get the same error message
with >  thunderbird --ProfileManager  
I can create a new profile and select it, but when I want to start thunderbird it crashes

---

### Post by walts48 on 2018-10-18
This is what I get launching Thunderbird from a terminal.

```
JavaScript error: jar:file:///usr/lib/thunderbird/omni.ja!/components/XULStore.js, line 65: Error: Can't find profile directory.
[calBackendLoader] Using Thunderbird's builtin libical backend
this should not be happening! arrgggggh!
The MsgHdrToMimeMessage callback threw an exception: TypeError: aPart is null
JavaScript error: resource:///modules/gloda/mimemsg.js, line 133: TypeError: aPart is null
this should not be happening! arrgggggh!
The MsgHdrToMimeMessage callback threw an exception: TypeError: aPart is null
JavaScript error: resource:///modules/gloda/mimemsg.js, line 133: TypeError: aPart is null
```

I suspect your problem isn't with Thunderbird, but something isn't right with your Ubuntu. Make sure everything is up to date there.

I'm using the default Thunderbird theme and the Adwaita (default) Ubuntu theme.

---

### Post by monkeybrain2 on 2018-10-18
I guess so. I do updates daily, but after the update 3 days ago thunderbird crashed at the start. I also have another pc running ubuntu 18.04 and thunderbird runs without any problems. The theme of both ubuntus and the thunderirds are the default themes. 
I thought maybe some of you could have an idea what these (error)messages mean.

---

### Post by jaweewo on 2018-10-19
Try to purge the thunderbird through terminal and then install it again.
You can do it using [HTML]apt purge thunderbird[/HTML]
And then install it again using  [HTML]apt install thunderbird[/HTML]

---

### Post by monkeybrain2 on 2018-10-19
I also tried that. Still get this error message :(

---

### Post by pqwoerituytrueiwoq on 2018-11-02
was thunderbird installed via snap or apt, you my be running a snap packaged version

as a alternative to fixing the real issue you can work around it by doing this
you can download it here: [https://www.thunderbird.net/en-US/](https://www.thunderbird.net/en-US/)
just extract it and run the thunderbird file inside

---

### Post by walts48 on 2018-11-02
> **monkeybrain2 said:**
> I also tried that. Still get this error message :(

Can you post a link to a crash report?

[https://support.mozilla.org/en-US/kb/thunderbird-crashes](https://support.mozilla.org/en-US/kb/thunderbird-crashes)

---

### Post by grozni on 2018-12-01
Did you able to fix the corrupted profile? I have exact same issue.
I'm using one profile across Ubuntu/Win machine. All was ok until some update, not sure when.

I tried deleting and recreating profile from both Ubuntu and Windows but I always end up with asking to setup new email account.
It does not import anything.

---


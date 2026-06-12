---
title: "IM client supporting account/channel settings based on current network"
date: 2013-08-19
forum: General Help
---

### Post by mickeelm on 2013-08-19
I'm using my laptop both at the office and at home, and in both places I use IM communication. At the office we have a channel for the project, when I'm at home it's more "normal" use, like hobby forums and such.

I'm looking for an IM client which can detect my current network (in one way or another) and act thereafter regarding which accounts/channels that should be active or inactivated. Right now I'm using Pidgin and I have to activate and de-activate accounts every time I change environment.

I like Pidgin's UI, so a plugin for it (or a basic setting that I've missed) would be my favourite option but if there are any other clients that have these possibilities I'd love to give them a try. It needs to support XMPP (and IRC but I figure most of them does).

---

### Post by Vaphell on 2013-08-19
i looked at my pidgin. In the status change config it allows you to customize status including 'offline' on a per account basis.  With that you should be able to create 2 pidgin statuses with different set of accounts (New..., checkbox + offline where necessary). Sure, it's not as cool as automagical change but easy enough.

---

### Post by mickeelm on 2013-08-19
Thank you for the answer! Although, the actual status like online/away/busy/offline isn't important, what I'm reaching for is for the client (be it Pidgin or some other client) to not connect at all (or vice versa). If I'm on my home network and my work account is active, it will try to connect but never succeed since this channel is only available on the office network. So I'd like a client feature that recognizes the network I'm on and from that decides which accounts to activate and deactivate.

---

### Post by Vaphell on 2013-08-19
.purple/status.xml stores default and user created statuses. I tested it a bit and it looks like the first one in xml is the default one (in other words setting the status moves it to the front).

create HOME and WORK profiles, WORK has only work account on and the rest set to 'offline', HOME has everything but the work account enabled.

whip up a script that recognizes network and depending on the result sets proper order in status.xml, put in startup or whatever. Run pidgin.

edit: reordering alone doesn't work
looking at the commandline parameters for pidgin there are options
```
  -c, --config=DIR    use DIR for config files
  -l, --login[=NAME]  enable specified account(s) (optional argument NAME
                      specifies account(s) to use, separated by commas.
                      Without this only the first account will be enabled).
```
obvious solution: if condition testing network, branching to pidgin -c $home_cfg and pidgin -c $work_cfg

---

### Post by mickeelm on 2013-08-19
Ah, now I found (sort of) what I was looking for - thanks for the help.

Although, it's rather .purple/accounts.xml that has the setting that I'm aiming at:

```
<settings ui="gtk-gaim">
<setting name="auto-login" type="bool">0</setting>
</settings>
```

The value of auto-login changes once you enable or disable an account. The settings in status.xml however only concerns the actual status - e.g. not the same as actually connecting/trying to connect.

Oh, now I read your edited reply and the -l option should definitely do the trick! Thanks a lot :) So if I just wrap a little script around my pidgin startup process that detects the network and add arguments to the -l options I should be just fine. Not exactly what I was looking for in the first place but will work perfectly fine :)

edit: Or, the -c option as you said. :D

---


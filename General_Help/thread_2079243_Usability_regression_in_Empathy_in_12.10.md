---
title: "Usability regression in Empathy in 12.10"
date: 2012-11-01
forum: General Help
---

### Post by berledotcc on 2012-11-01
I recently installed 12.10 on a machine and immediately noticed several problems with Empathy.

[LIST]
[*]The size of the contact list can no longer be changed, and defaults to the largest possible setting available in 12.04. You have to scroll for days to reach the end of it.
[*]When you click on an incoming message in the messaging menu, Empathy no longer pops up to show you the message. You have to click into Empathy manually and then click on the new tab.
[*]There is no longer any counter on the launcher icon showing how many people have been trying to contact you. So if you did not look at the screen for whatever reason, there is effectively no indication that you have actually gotten any message.
[/LIST]
This just makes Empathy utterly useless to be honest. And it leaves me with 3 choices:

[LIST=1]
[*]Switch back to 12.04. I dont really like the idea of doing this, because there are several new features in 12.10 I do like a lot. The web apps for instance is exactly what I have been wanting for a long time.
[*]Fix Empathy. Given that Empathy is a GNOME project, it feels like a bit of an overwhelming task to try to even find the right people to talk to, try to convince them that they have made mistakes, figure out what is caused by Ubuntu and what is caused by GNOME, etc. Or even maintain my own copy of Empathy in a PPA. Which I do not really want to do either.
[*]Fix Pidgins integration with Unity. The main reason I switched from Pidgin to Empathy in the first place was the poor integration with Ubuntu/Unity. The plugin that provides the integration leaves a lot to be desired. But now that Empathy is an even worse choice, it might just be worth it to have a look at making Pidgin integrate smoothly. As in, it might be less work.
[/LIST]
Clearly, alternative 1 is the one with the least amount of work involved for me. In all likelihood, 2 is going to be the most amount of work. Im not sure if 3 is the right thing to do either.

My question to the forum is, what do you think I should do?

(And yes, bug report has been submitted)

---

### Post by valentinoconesa on 2012-11-04
I'm completely agree with you.

It is depressing to use a new version of Ubuntu and having a great loss of usability in empathy.

I'm going to try the switch to Pidgin... let's see

---

### Post by screaminj3sus on 2012-11-10
> **valentinoconesa said:**
> I'm completely agree with you.

It is depressing to use a new version of Ubuntu and having a great loss of usability in empathy.

I'm going to try the switch to Pidgin... let's see

pidgin is even more broken right now. late in the 12.10 cycle they up and totally changed the message indicator API so many app including pidgin still haven't been ported. so currently in 12.10 pidgin has no unity integration at all

---

### Post by berledotcc on 2012-11-30
A little update here. It seems like the most important problem has been fixed now. Empathy will show that you have incoming messages.

---

### Post by CrusaderAD on 2013-01-23
Does anyone know how to reduce the size of the contact avatars in the buddy list? They're huge. Looks ridiculous.

---

### Post by jbx999 on 2013-03-01
Yes, they're ridiculously huge and there seems to be no option to change them to the old ones.
Also, there doesn't seem to be any way to sort by status. I get most people in Idle status now at the top instead of who is online!

---

### Post by Bachi on 2013-05-07
Seems the option for the compact contact list was removed with this commit: [https://git.gnome.org/browse/empathy/commit/?id=f58d68ddddf15dfe4e0d49af86e2add3c606316e](https://git.gnome.org/browse/empathy/commit/?id=f58d68ddddf15dfe4e0d49af86e2add3c606316e)
I don't see the reason why, and yes it's nearly unusable. We should ask them for the reason.

---


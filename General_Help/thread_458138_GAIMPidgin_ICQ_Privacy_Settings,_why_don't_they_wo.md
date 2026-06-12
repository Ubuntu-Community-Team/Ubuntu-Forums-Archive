---
title: "GAIM/Pidgin ICQ Privacy Settings, why don't they work?"
date: 2007-05-29
forum: General Help
---

### Post by deadlines on 2007-05-29
See subject, I am sick to death of receiving requests from spammers to authorize them for my contact list EVERY single day.  Every time I go into privacy settings for ICQ in GAIM or Pidgin and set it to "Allow Only Users On My Contact List," a couple of hours go by and suddenly there they are bugging me to allow them onto my list again.  I go into privacy settings and the ICQ setting is set back to "Block Only the Users Below."

Does anyone have any idea how the heck to make this setting stay permanently?  This is just really annoying as they seem to have some trick to override the setting and set it back to the default.  Any help would be most appreciated.

---

### Post by kuja on 2007-05-29
Umm, here's a trick that *may* work. Open up gaim's config file (preferably with gaim closed) which should be a hidden file in your home directory (or a hidden directory, same difference really, that's where you'll find it at any rate). 

Look for the setting and set it manually, may work. If you're unsure what to set it to, try taking a  look at it after having changed it and before it sets itself back

I hope this'll work for you.

---

### Post by deadlines on 2007-05-29
Sadly I've tried that already, but thanks for the suggestion.  To my knowledge this is a known bug that was supposedly fixed in Pidgin 2.0.0beta 7, but I'm still encountering it.  I actually wondered about trying to chmod the config file once I got it setup the way I wanted it, but no luck on that front either.  I think the client just builds a new config file. :/

---

### Post by kuja on 2007-05-29
Odd, that was actually the next thing I would have suggested too. I wonder why removing write access to the file (for all users) and/or changing the files owner also wouldn't handle that, that way it can't delete, modify, or re-create the file ... period.

---

### Post by deadlines on 2007-05-29
Sigh, and of course I just had two more Russian spammers request authorization.  This is literally a daily occurance, I am sooo annoyed!  Maybe they think I'm located in Estonia or something, this is just ridiculous.  I'm going to do some more digging on the actual project site for Pidgin and see if there's anything more on this extremely annoying issue.

Update: I installed Pidgin 2.0.1 this morning, so far the ICQ privacy settings *seem* to be working.  Keeping my fingers crossed on this, I'll update again in a few days on whether or not it randomly changes the settings back to, 'Block Only the User Below.'

Update 5-31-07: Fixed! Well, the latest version of Pidgin (2.0.1) seems to have finally addressed this very annoying issue.  If you're running into it, upgrade and you should be good to go.

Update: 06-05-07: NOT fixed, there is apparently a way this setting can be remotely overridden as that is just what continues to happen.  Settings stays, but eventually I'm getting some auth request from a spammer, go into the settings, it's set back to "Block only the users below"

---


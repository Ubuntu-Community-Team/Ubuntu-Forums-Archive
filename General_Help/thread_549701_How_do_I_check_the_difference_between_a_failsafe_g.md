---
title: "How do I check the difference between a failsafe gnome session and a regular one?"
date: 2007-09-12
forum: General Help
---

### Post by ev0 on 2007-09-12
I'm trying to find out why Lotus Notes 8 only runs with failsafe gnome but not a regular session. I need to check what part of the regular startup causes the Notes crash so I want to find out what starts with a regular session that doesn't start with a failsafe.

Can anyone please tell me where I can check the startup script for failsafe gnome and a regular session? Thanks!

---

### Post by Lylepalooza on 2007-09-12
One option you might consider is typing dmesg in terminal in failsafe mode, and then dmesg in normal mode.

You might also try and type dmesg again in terminal after trying to load Lotus in each.

I think that would be a good starting point until someone comes along with a better option :)

EDIT: I should mention, after typing dmesg in console after trying to load Lotus, you should notice a difference to the message at the very end. IE The last few events in the list should be different.

---


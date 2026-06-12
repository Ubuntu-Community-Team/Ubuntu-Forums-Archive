---
title: "Need help with debugging Dwarf Fortress for Linux keyboard error. Weirdest error yet"
date: 2013-11-29
forum: General Help
---

### Post by cecilx22 on 2013-11-29
I'm not looking for an answer (but I'll take one...), but more for just where to start with this one. It's a VERY weird error, and I'm not sure where it's coming from.

Short version:
Upgraded from 13.04 to 13.10, and now Dwarf Fortress for Linux is experiencing corruption of keyboard input.

Long version:
As above, I had been running 13.04 for a long while, no errors what so ever in the game. Everything worked great. Now, I'm getting REALLY weird keyboard input corruption. I'll do my best to describe it:

1) Going along, using keyboard as normal to navigate around map, game menus, etc, when suddenly, the game starts acting like a key is being pressed over and over, repeatedly.
2) I'll press that key again, and the repetition stops, but then things get even weirder.
3) Lets say that the left arrow key had been repeating. After stopping it from repeating, I start pressing the up arrow (for instance). After a random number of keyboard events, the game suddenly responds as though I had pressed the left arrow key again.

I'm no guru on how the xinput system is set up, but is seems to me that they key-up commands are perhaps getting lost/mis-ordered? I'm assuming, since this isn't an issue EVERYWHERE, that this is a problem with the game itself... but at the same time, various googleing results about this bug had gotten me know where, so I don't think it's specifically the game either. Hell, I don't know what might be involved or causing the problem... SO

1) What things should I list out that might be relevant? (WM, compositor, etc?)
2) The game runs in a terminal (and is started in another terminal) how do I tell what the game terminal is (xterm, gnome-terminal, proprietary, etc?)
3) Can you think of any way to 'watch' what's happening with the xinput as it happens?
4) Help?

Thanks!

---


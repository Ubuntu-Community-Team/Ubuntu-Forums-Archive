---
title: "smb shares integrated into one folder"
date: 2006-11-10
forum: General Help
---

### Post by RageAgainstThis on 2006-11-10
Ok basically what i am doing is creating a samba server that will share movies and what not for use.  I use xbmc to stream movies to my television and would like to have all my movies in one directory.  I would like to combine two folders that are on completely different drives and have them show up on samba as one folder.  So movies(disca) + movies(discb) = movies(discC).  I am not sure if this is possible it would just be convienent for me.  And maybe one day i can get a harddrive that is close to 1 tereabyte to take care of this problem 8) .

---

### Post by broncavfan on 2007-07-16
I'm only just getting a good grasp of linux and ubuntu but I'm in the same boat.  I use my computer to as a server so that when I want to watch movies I just turn on my XBox and fire up XBMC.  I haven't quite gotten to the point where I need to have 2 hard drives sharing into 1 folder, but I will be soon, so I figured I'd give my two cents.  All I did was make a link to the files and combined them all into 1 folder (as a test, of course).  XBMC seems to play the files just fine, so when I get to the point of needing another hard drive I think that's what I'll do.  You can link files in bash using the command "ln".  You can also right click a file and select Make Link, but I think that way would be the long way.  You would probably want to use bash and make a short script to do all the files in one fell swoop.  Unfortunately I don't know enough about bash and scripting to give you an example, but I would imagine it would be a fairly simple 'for' routine.  It would also be nice to have the link automatically update whenever you add a file, but I know that I'd be happy enough just running the script each time I wanted an updated list.  I hope this helps, and if you have any luck you should let me know because like I said, I'm going to be in that same spot fairly soon.  Good luck!

---


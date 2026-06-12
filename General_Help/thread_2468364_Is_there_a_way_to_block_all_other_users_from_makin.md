---
title: "Is there a way to block all other users from making ANY changes to my computer?"
date: 2021-10-26
forum: General Help
---

### Post by 777funk on 2021-10-26
Newb question for a long time Ubuntu user but I am having a problem with the occasional folder being moved or deleted or even Thunar's Bookmarks disappearing on me.

I'd like to be the only admin on my machine WHILE allowing other users to copy files from the computer to say their MP3 players etc. I don't mind if they download new files but I would like to be the only one to change folder structures or DELETE files. 

Is this possible?

---

### Post by The Cog on 2021-10-26
That sounds to me as though they are logging onto the same account that you are using. You shouldn't have that problem if you give them all separate accounts. Then they would be able to do stuff in their own home directory, but not yours. Or am I missing something?

---

### Post by 777funk on 2021-10-26
> **The Cog said:**
> That sounds to me as though they are logging onto the same account that you are using. You shouldn't have that problem if you give them all separate accounts. Then they would be able to do stuff in their own home directory, but not yours. Or am I missing something?

Good thinking! This would probably be the best solution. 

I so far have kept it under a single account. This way they can access my music, videos, etc. I think I'd like to keep it that way but I just don't want the kids to be able to make changes. What I'm finding is deleted files and directories accidentally dragged and dropped into other directories. It's made my life a little more complicated than I'd prefer.

I could just say... get your own computer (or account) and maybe that's the best way. I suppose I could copy the folders they use to another account.

---

### Post by dragonfly41 on 2021-10-26
I suggested separate accounts in your twin post. But you can create a hybrid system.
Folders shared by all the family plus separate accounts for important individual stuff.
Or shared dropbox account synced to your master account..

---

### Post by grahammechanical on 2021-10-26
You are the only administrator on that machine but you are allowing other people to use the computer under your log in. So, of course they are able to do the things that the OS allows the standard user to do and it is being done in your account as if it was you. As far as the OS is concerned it is you doing this stuff. Imagine what they could do if they get the knowledge of your password. Then they will become the administrator and do much worse damage.

Do you do online banking? Do you allow the web browser to store your password? Then anyone using that machine can access your online bank account. The same thing will happen to all online accounts where the web browser stores the username and password.

Change your username and password. Create at least one other account. Copy to that account any music/video files you are happy to give these persons access to. Do your children have friends? Do they come to visit? Do the friends have access to the computer. You have no idea what kind of files and images could be downloaded on to this computer and under your username.

Regards

---

### Post by GhX6GZMB on 2021-10-26
I always have(at least) two accounts on my machines: my own with sudo/admin rights. No one gets access but me.
And a "myguest" user account for visitors and others with a simple password, eg, "myguest" and group "myguest" (or whatever name you like).

You seem to want to allow other users to have access to your /home, but want to prevent them from making changes.

One way is to change the access permissions for "other" in your /home directory, and you should do this anyway for security reasons. The newest distros do this from birth, I believe from 20.10 and newer.

After you've made the "myguest" account and done a logout/login to create the new user directories, login as yourself. In a terminal issue the following command (**make sure you're in /home by issuing cd $HOME first, otherwise this is dangerous!!!**):

**sudo chmod o-w -R ./* ./.[!.]***

This will remove write rights for all "other" users, which "myguest" is. Read will still be possible, and the execute flag will also stay to allow directory transversion. Modifications are out, though.


Personally, I wouldn't choose this way, but instead copy the files and directories of interest to the /home directory of the "myguest" user. That's the other option.

---


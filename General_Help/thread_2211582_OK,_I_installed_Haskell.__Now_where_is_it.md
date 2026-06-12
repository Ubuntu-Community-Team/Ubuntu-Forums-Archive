---
title: "OK, I installed Haskell.  Now where is it?"
date: 2014-03-16
forum: General Help
---

### Post by birrell on 2014-03-16
I needed Haskell, so I went to the Haskell website and downloaded software as a tarball.  I used synaptic program manager to install the Haskell Program.  Now how do I find it?  Run "Haskell" does not work.  I do not see a Haskell directory.

Is it rude to ask why Linux makes it so hard to install and use programs?

Thanks

---

### Post by oldos2er on 2014-03-16
Moved to General Help.

---

### Post by 3rdalbum on 2014-03-17
Linux provides everything to make installation easy, although some program developers go out of their way it seems to make the installation of their programs difficult for new users.

Go into Synaptic and right-click on the Haskell package. Choose Properties and click the Installed Files tab. Anything inside a /bin directory is runable.

---

### Post by birrell on 2014-03-17
Thank you for your thoughtful reply.  I looked in the properties tab.  I opened the Thunar file manager and navigated to that bin directory.  I chose several promising files, like "runhaskell" and "ghc" and right-clicked on them and chose execute.  Nothing happened.  I tried the right-click menu's run command, and gave the full path of (eg) ghc.  Nothing happened.

Did I forget the secret handshake?  If I were working in Windows, I would have been installed and running hours ago.  I know this because I downloaded the Windows version too, and I WAS installed and running hours ago, even with having to bring in a new editor.  Has no one addressed this installation issue in all the years linux has been around?

Thank you for taking the time to answer.  That was kind.

---

### Post by mastablasta on 2014-03-17
i would say you open launcher (in KDE it's Alt+F2, but i don't know how it is done in unity) or terminal and type haskell and hit enter. that's how they normally do it in linux applicaitons.

unless they install the hwole thing in home in which canse it would be ./haskell to run it or something like that.

---

### Post by 3rdalbum on 2014-03-17
Try typing 'runhaskell' in the terminal. I should have mentioned that you would type the file name into the terminal, sorry.

As I explained, it's not a Linux problem. It is a problem with some app developers. "Oh, all Linux users are geeks and all prefer to use the terminal, let's not bother making my program easy to install." Unfortunately I can't use the swear word on this forum but the attitude of those developers really Sh's me. Fortunately it is not as common these days, and more application developers are using Linux's easy installation features because they realize not all Linux users are supernerds. Installing and running Linux programs is usually easy now.

---


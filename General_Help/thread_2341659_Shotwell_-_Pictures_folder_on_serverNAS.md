---
title: "Shotwell - Pictures folder on server/NAS"
date: 2016-10-30
forum: General Help
---

### Post by Roasted on 2016-10-30
Hi friends. In our household, I have a 6TB file server (Ubuntu Server) in the basement. This acts as a central hub for all of our data. I also have autofs running on all systems, which automatically mounts a smb share when the user, or any application, requests access to the particular 'data' folder.

For example, I have Clementine's music folder mapped to /media/user/vault/music. When you open Clementine, you'll see "vault" get automatically mounted like magic. This results in myself or any other user accessing the music library over the LAN with Clementine as if the music were local. This is mega handy given our systems, even our laptops, rarely leave the LAN, so we can benefit from cheaper/smaller SSDs in the computers by not having to try and shove several TB of important documents, pictures, and music on each system.

The same is true for pictures. Shotwell looks for pictures in /media/user/vault/pictures. It automatically updates the library as well. It handles many tasks quite gracefully. For example, yesterday I took some pictures on my phone (which automatically uploaded to my Nextcloud server, then back down to my laptop), so within Shotwell I ran "Import from folder" and selected "copy photos" so the pictures get copied from my laptop/cloud folder/instantupload TO the server.

On my wife's laptop, I open Shotwell, and in short order the new pictures I took on MY phone, which synchronized automatically to MY laptop, are suddenly displayed on her laptop in Shotwell. This is great. Works awesome. Love it.

But as I look deeper into our Shotwell photo library, I want to make more use of certain features, such as tagging, merging events, etc. As a test, I just merged two events together. The event on my laptop reads October 19-October 20. When I go on her laptop, though, it does not yield these same changes. October 19th is still its own event, and October 20th is still its own event.

Any idea how I can make this a more graceful situation? I find it wildly helpful that Shotwell automatically stores the pictures by year/month/day folders and provides us an excellent interface to view/navigate the pictures, but the ability to merge all 7 days of a beach trip together and those changes be shown on all systems would be wildly beneficial.

Thoughts?

---

### Post by DieB on 2016-10-30
I guess this happens, because every system has its own library file and separately imports the photos, the library file resides in ~/.local/share/shotwell/photo.db - I believe that this is the source of your question, yet I do not have any clue how to merge changes between different libraries, unless each and everyone has the same photos, then I would copy the photo.db to your vault/pictures/ and symlink it to .local/share/shotwell

---

### Post by Roasted on 2016-10-30
> **DieB said:**
> I guess this happens, because every system has its own library file and separately imports the photos, the library file resides in ~/.local/share/shotwell/photo.db - I believe that this is the source of your question, yet I do not have any clue how to merge changes between different libraries, unless each and everyone has the same photos, then I would copy the photo.db to your vault/pictures/ and symlink it to .local/share/shotwell

Everybody does have the exact same photos, as the photos in question originate from the same exact 'source' for all machines -- the file server. That said, your suggestion on symlinking the db may be the key. Given autofs automatically mounts when called upon, it stands to reason that it would auto-mount the share to retrieve the Shotwell db whenever needed. Makes sense.

That said, this actually brings up more questions.

1) On more than one occasion, I've read posts on the forums where users had issues logging in, as they seemingly had a corrupt profile somehow. The fix is normally to nuke some sort of .folder or .file in their home directory. Sometimes, this can get quite difficult to diagnose, resulting in the user simply nuking all .files+.folders. I experienced this just last week on my desktop, so I get it. Nothing I tried worked, and after 20-something attempts followed by reboots and attempted logins, I moved (as I hate deleting unless I am positive) all .files/.folders outside of my root home directory -- and it let me log in again so I could set my icon order up, etc. Thing is, that would suggest that you'd lose the db, thus losing these tags, merged events, etc. That sounds like a lot of work to build up again. How is that... okay?

2) Take the file server out of the equation. Let's say I'm simply storing everything on one computer. I work on my tags, merge my events, and set up Shotwell exactly the way I want. But let's say I'm a fan of fresh installs with a fresh home directory. There's people out there who swear by this -- lots of them. Those users would miss out on these changes unless they specifically think to retrieve the db for Shotwell, as relying on Shotwell to magically make them appear again WITH tags, WITH merged events may not be the end result. Speculation on my part, but it's a likely thought worth entertaining.

I guess this actually brings up more questions than answers. I would have thought that data is written to the files for these tags, for these merged events, etc. I do see with some photos tagged as Cheese that under file properties, image tab, it says "Keywords: Cheese", so perhaps *that* data is written to the file. But merged events? With the photos in an event I merged last night**, I don't see any reference of the two independent events being 'merged' as the file properties level.

Perhaps it stands to reason that the point/design/planning of the merged events feature just simply doesn't write the data to the files** and thus works against the idea of multiple systems sharing that same pool of pictures. Despite this, Shotwell clearly does a good job on picking up new photos from the other computers when they each share the same data location -- and this makes a lot of sense, as Shotwell can "watch" your pictures folder for changes, thus allowing you to 'drop' photos in the pictures folder and Shotwell just magically sees that and updates itself. This functionality is why I'm seeing success with importing pictures to Shotwell on my laptop (thus copying the pictures to the file server), and when my wife fires up Shotwell on her laptop, it scans, sees the new photos, and displays them accordingly.

**It's worth mentioning that in Shotwell's preferences I -do- have "write metadata and other information to files" checked.

---

### Post by DieB on 2016-10-30
about 1) I heard about this "solution" too, yet never had to delete all files and as you wisely did, you have a backup and can copy your files back one by one, and therefore reverse engineer the original problem - plus usually/always the problem does not originate in .local

about 2) those people normally carry over their dot-files (aka hidden-files), at least back them up - in this case you just would have to create a new symlink in .local to your photo.db on "the vault"

---

### Post by Roasted on 2016-10-30
I suppose so. I guess I was putting more hope that Shotwell was figuring out its amazingness based on the actual picture files themselves as opposed to a separate set of files (the db files).

Next question I'd be curious about is how resilient Shotwell would be with multiple users hammering the same set of database files. I would suspect it would work fine, though let's toy with some what-if's. What if... my laptop is fired up at the same time my wife's is and we're both tagging things in Shotwell? With a symlinked db, and thus two systems editing the exact same db file at once, something makes me skeptical it would fly without issue.

I think I may pump the brakes on this magnitude of features, such as the merging of events. The tagging of events seems like it would work well given it writes the data to the files (i.e. keyword: cheese, etc). This may come with its own benefits that are floating around in the back of my mind, though I'd have to test further to see for myself.

Appreciate your insight, DieB. Thanks for being awesome. :D

---


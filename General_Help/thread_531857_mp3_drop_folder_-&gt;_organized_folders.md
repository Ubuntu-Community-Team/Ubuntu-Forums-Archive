---
title: "mp3 drop folder -&gt; organized folders"
date: 2007-08-22
forum: General Help
---

### Post by chirsjennings on 2007-08-22
I have a Ubuntu 7.04 server setup here at home and I want to setup a file/music server setup. 

I want to be able to have networked Windows, Ubuntu, and Mac computers drop properly tagged mp3s into a folder on my server which are moved from a "drop" folder into organized folders on the server. 

Ideally I would also like the option to synchronize the organized mp3s between some of these computers (as some are laptops) and have changes that are made off the server get reflected back to the server. 

I was thinking some kind of weird CVS or SVN system might work for the synchronization part, but I don't have any experience with that. Thoughts? Ideas?

What suggestions do the experts have?

---

### Post by kidders on 2007-08-23
Hi there,

> **chirsjennings said:**
> I want to be able to have networked Windows, Ubuntu, and Mac computers drop properly tagged mp3s into a folder on my server which are moved from a "drop" folder into organized folders on the server.Depending on how elegant/secure you wanted something like this to be, it could be quite straightforward. There's quite a number of basic utilities capable of parsing MP3 tags, any of which you could use in a script, to move things out of your dropbox & into the right place. If you were feeling ambitious, you could hook the process into your server's FAM/Gamin libraries.

> **chirsjennings said:**
> I would also like the option to synchronize the organized mp3s between some of these computers (as some are laptops) and have changes that are made off the server get reflected back to the server.This would be far more complex, and (imo at least) not worth pursuing, unless you're prepared to spend quite some time working on it. Again, the elegance of the solution would very much depend on how much time/expertise you've got.

Having considered this particular problem for a few minutes, I can't help wondering if WebDAV would be the way to go. By putting a layer of, say, PHP between the real files and the clients, you would have completely arbitrary control over locking, versioning, serialisation, and so on. Essentially, you would be exposing an entirely synthetic filesystem to your clients, that wouldn't necessarily reflect the true state of the server's local filesystem.

Other, perhaps more natural solutions might involve svn, rsync, and similar utilities, however the client-side implementation of many such options might be a little hairy.

For me, the ideal would be to blend your two ideas into one. Consider, for a moment, that you'd written a home-grown, scripted WebDAV implementation, running off a local web server.

[LIST]
[*]Given that you need Windows, Linux and Mac client-side compatibility, the only viable alternative filesharing protocol would be Samba, because going down the road of sharing the same files over multiple protocols simultaneously can lead to odd behaviour in high-volume environments, or those involving multiple character sets. Using Samba would expose your Linux & Mac clients to all the irritating, pointless restrictions of the Microsoft world.
[*]You could decide not to bother with the first part of your problem (ie physically sorting music on your filesystems) at all. Instead, your WebDAV server would synthesise the appropriate directory structure, based on ID3 tags. As a result, a client-side ID3 tag modification would effectively cause a file to "move" instantaneously from one directory to another.
[*]You would have the flexibility to be very smart when it comes to odd combinations of circumstances, such as what should happen when one user is playing a file while another user modifies or deletes it, how rapid successive modifications to the same file are handled, and so on.
[*]You would also have the freedom to *properly* filter filenames for characters that don't play nice with whatever OS happened to be accessing the shared music at any given time. When I say "properly", I'm thinking of how Samba deals with filenames that Microsoft dislikes ... just about anything would be preferable to that!
[*]As an aside, since WebDAV isn't dependent on mDNS, broad/multicasting, etc., you would have the freedom to open your share more easily to machines that aren't on your LAN.[/LIST]If, however, you were thinking of something a little less ambitious, two possibilities come to mind:

[LIST=1]
[*]Making your music share read only, and forcing clients to cache any modifications they make locally for later synchronisation, at which time any conflicts would be resolved. This sort of approach makes conflicts more likely however, since there could be a considerable lag between the time client #1 makes a change and client #2 sees it reflected in the shared music.
[*]Inventing some way for your music server to recognise a file it *used* to host, after it had been modified. That way, users could steal a file, tweak it & immediately throw it into the server's dropbox, confident that the server would be smart enough to replace the original copy with the new version. Exactly how to do that would be a matter of personal choice. You might, for instance...[/LIST][INDENT][LIST]
[*]Explore the MP3 file format specification for clever ways of adding spurious data (ie a serial code) to files in a way that would be ignored by music players *and* preserved in the event a file were truncated, passed through a filter, re-tagged, etc.
[*]Reserve part of all ID3 tags for use as a UUID. A file in your server's dropbox with the same UUID as one it already knows about would be considered its replacement.[/LIST][/INDENT]
Anyhow, I hope this post gives you some ideas ... even if you don't like any of the ones I came up with.

---

### Post by chirsjennings on 2007-08-23
Thanks for the thorough reply! You have given me quite a few options to mull over. 

I am not really worried about security as this is a home network and the server is secure from the outside world. Could I get the names of some of these mp3 tag parsers? I am almost completely new to Linux, so I am not familiar with much. I took a quick look at FAM/Gamin and it looks interesting, I guess based on what I end up with for a solution I may have to take a deeper look at it. 

I like your idea to use part of the ID3 tag for identification. I was thinking of adding an ID formatted like "CJ#14237" to the comments field. this way the comments field could still be used because I could tell a script to look for my special formatted ID. 

So now the problem has evolved a little. I am going to break down my current idea into components.

Components
[LIST]
[*]Server: music folder with folders containing mp3 files
[*]Server: mp3parser
[*]Server: UUID database
[*]Server: Synchronization Software
[*]Client: Synchronization Software
[/LIST]

Whenever a Client adds/updates a file to their local music folder and a synchronization is called the following needs to happen on the server:
[LIST]
[*]The file is added to the music folder on the server
[*]A program watching music folder for any changes runs the mp3 parser on the new file
[*]The mp3 parser checks the comments field for UUID
[LIST]
[*]If found, check a database of UUIDs for the location of the old version of the file and over write it
[*]If not, add UUID to comment field in the file and update to UUID database
[/LIST]
[*]Mp3 parser checks tag and organizes the file into the appropriate artist/album structure and updates UUID database
[*]Upon the clients next sync the file they added is deleted and the organized/UUID tagged file is added instead
[/LIST]

The tricky part (IMO) of this is the last step. Any ideas on how to resolve this? And how about suggestions for the synchronization part?

---


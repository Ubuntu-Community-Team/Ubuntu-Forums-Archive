---
title: "At home server and workstation configuration of users and /home folder"
date: 2013-09-08
forum: General Help
---

### Post by jonnymd on 2013-09-08
I'm new to Linux/Ubuntu. I've played with the system for years and have a file server that's been running Ubuntu for a few years.  Now I'm ready to convert my desktop workstation as well as my wife's.

I'm looking for feedback on my proposed configuration as well as pointers/tips for configuring permissions for users/group.  Previously I used my file server just for serving my large movie/tv show files (~3TB) to workstations and set top boxes.  I would now like to use it to store ALL files from my wife and myself.  I'm planning to create two users (J & K) with their own individual home folders, so the users have independent configuration settings stored as well as files.  These home folders will naturally include the individual user's videos, docs, photos, downloads, and music.  They will each have full permission to the other user's home folder (perhaps better to give permissions just to the five individual folders of videos, photos, music, docs, downloads?).  They will also both be able to access the shared movies/tv shows (on separate hard drives mounted to /mnt/movies and /mnt/tvshows).

Then each user will have their own workstation (I'm thinking about trying out raspberry pi's or something like it - not sure if they are powerful enough).  The workstation will have both user accounts (J & K), with /home folder information mapped to the respective network (file server) location.  The purpose is to centralize all the data, both files and settings (for simplicity in 'where' files reside and backing up, both locally and via crashplan.com).  By having it all centralized I can share individual music, photo and video collections using plex or other media servers and have the same library accessible to both workstations, as well as all mobile devices (laptops, smartphones, tablets) and set top boxes (3 roku's and a smart tv).  The other purpose is to have an organized foundation for expanding space (on a more robust server with added on HDD) and for future users (likely adding children user accounts in the next few years).  Primary use for all users is internet "surfing" and basic document creation with some minimal photo manipulation through Google Picasa. I'd like the setup to be consistent for the user experience, regardless of which "raspberry pi" workstation they are sitting at (my wife logged in as herself on my workstation or visa versa).  I'm also looking to eliminate the need to identify which files are where, especially with a growing number of devices everyday.  

Ideally, a lot of these files could someday be 'centralized' via a cloud configuration but to-date it is too $$$ to do so in a comprehensive way (include photos, music and especially video).  Not to mention it doesn't centralize setting/configurations.  The [kickstarter "plug" (renamed Lima)]("http://www.kickstarter.com/projects/cloud-guys/plug-the-brain-of-your-devices") looks to be appealing, but can be added to the setup I'm describing.  The vision is to have a feel within my home similar to what Google Chrome OS provides without being limited to just chrome os and internet apps.  The thought of using chromebooks for the individual workstations HAS occurred to me.  For now this seems to be a decent hybrid approach (until the cloud solutions offer a more universal approach to files/settings).

I'd like feedback on several parts: First, does this seem like a good setup or is it overly complex?  Does centralizing all the information on a server (with more cpu power and HDD space) yet keeping most parts individualized by user account make sense?  Is there a better way to achieve the primary goal of centralized yet individualized data, both settings and files?

When configuring such a setup, I assume permissions to other user's /home folders can best be done by adding both users to a common group and giving that group permission to all /home folders (or perhaps just the subfolders within the /home folder, not sure which is more advantageous).  Regarding the workstation user profiles, how do I set it up so that their /home folder is essentially the network or file server location?  Will their be harm done if the network location becomes unavailable (server gets shutdown or unavailable by network for some reason)?  What would be the 'fallback' /home location in that scenario and could it re-sync changes once the network share comes back online?  These are some of my concerns.

It seems that the best way to configure such a setup is with symbolic links to the network share.  Is that correct?  If so, how is that best accomplished?  For network share permissions, would I simply do SAMBA shares of those home folders under the usernames J & K and since the workstations have the same accounts (username and password identical) they would connect fine?

Any and all feedback would be appreciated.  I'm looking for the most flexible, simple and organized setup after a decade of computer growth as a technology enthusiast wanting to simplify home management (in particular file management - and needing a backup plan that WORKS).  Thanks in advance.

---

### Post by bewareofthephog on 2013-09-08
You might want to [read this]("https://help.ubuntu.com/community/SingleSignOn"), it's pretty comprehensive on explaining how to have a setup similar to what it seems like you're wanting to do.

Secondly, you said you're wanting to use a raspberry pi.  If you're wanting to use a raspberry pi as the workstation then I would suggest creating a Ubuntu Desktop with SSH access.  Then on the raspberry pi have it remote desktop into the "Desktop Server".  This will offload everything making sure your Pi is only being used to display what's been processed.  I do a lot of hobby work on Pi's and I think this will be the best approach if you're wanting to use them as the workstations.

If you're just wanting to share file to your /home then I think you should be able to setup a samba share in fstab, though I've not done it successfully yet so I can't provide any information on that one.

Weather or not the Pi is powerful enough as a workstation depends on what you're going to be doing on them.  If you're just surfing facebook and listening to music you *should* be ok.  Personally if it was me I'd want to offload everything to the "Desktop Server" by remoting into it.  Just some food for thought.

As a disclaimer I doubt I'm the best resource for a project like this but I wanted to get my 2 cents since I love little hobby projects like yours.  Make sure to keep this thread updated I'd be interested to see what direction you went and what the outcome was.

Edit:
After a bit of googling I haven't seen any ARM builds of Ubuntu yet, but you might want to keep an eye out for it.  When it's released you could do something more along the lines of that SSO link I have at the top.

Also, since you mentioned a backup plan that works, have you looked into [rsync]("https://help.ubuntu.com/community/rsync")?

---


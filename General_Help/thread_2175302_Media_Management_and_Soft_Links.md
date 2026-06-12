---
title: "Media Management and Soft Links"
date: 2013-09-18
forum: General Help
---

### Post by skibum3027 on 2013-09-18
I'm having some trouble merging 4 folders of TV shows together using soft links. I've gone through tons of forum posts here and elsewhere and I can't figure out how to create a soft link that will merge the subfolders from one location with the subfolders from another soft link. 

I know circular soft links are a dangerous path, but I'm trying to dump 4 folders into one. I don't need to (as far as I know) redirect that folder again in any way, so it shouldn't be a problem.

The machine I'll be working from is my server and is set up to dual boot between (sometimes k)ubuntu and windows, so I'll take whatever assistance anyone can provide in any operating system, but it spends most of it's time booted into ubuntu providing me with all my movies, tv shows, music, documents, and pictures anywhere with internet access.

The folders in question are on an NTFS drive. It just works better with Windows in my experience, so I'd like to stick with NTFS if possible.

I want to keep the files separated because they are from different sources. I have one folder for shows I've ripped to the hard drive from my Blu-Rays (G:\BluRay Rip), one for my DVD's (G:\DVD Rip), one for HDTV I've recorded (G:\HDTV Rip), and one for standard definition TV I've recorded (G:\TV Rip). "G:\" might be better known as sdd here, but I wasn't really sure how else to indicate that these folders were at the "root" of the drive, if that's the right term. (Nothing to do with root access)

I want to use soft links to merge these folders into one folder, G:\TV Shows. Each of the folders contains a subfolder for each TV show in the category. Each TV show folder contains all the metadata for the series, as well as a subfolder for each season I have in that category. While I always have every episode of each show, they are usually spread out over at least 2 of these folders. 

For example, I have the first two season of Game of Thrones on Blu-Ray, but I also have HDTV recordings of season 3 that I'll delete when I get it on Blu-Ray. So in this example, I want to merge G:\BluRay Rip\Game of Thrones with G:\HDTV Rip\Game of Thrones and create G:\TV Shows\Game of Thrones. Since all the metadata is identical, I don't care which set is displayed. I just want G\TV Shows\Game of Thrones to contain all 3 seasons without actually relocating the files.

I won't be back with the actual machine until later tomorrow, but if there's any commands anyone would like me to run, let me know and I'll post them as soon as I'm home. I can provide additional information without running commands before then if there's any gaps in what I've provided.

Thanks in advance for helping!!!

---

### Post by TheFu on 2013-09-18
I'm positive that soft linking either folders or files works fine for XMBC across ext4, ext3 and JFS file systems.  I would never think to attempt that with NTFS involved.  I was under the impression that links in NTFS were only good with Explorer involved, not at the file system level.

If you want to link folders within the Linux file systems, just use 
**ln -s source target** - where the target can be optional if you like the name.  Both directories and files are supported. Regex can be used to softlink multiple files or directories in the same command.

It is usually easier to work with directories and files that DO NOT have spaces too, otherwise, you'll need to quote and/or escape the spaces in all your commands.  I use underscore_characters_to_make_it_easy_to_read. XBMC and other media players will ignore them by default.

Other options are to rename all the files to include the source/resolution, then put them into the same folder.
Or make subfolders under the show/episode name for the source/resolution and put the files into those.
Eventually, you will probably outgrow whatever a single disk can hold, so being able to add storage "volumes" into your directory structure would be a good idea too.

And forget about drive letters. Those don't matter in Linux.

So the easy answer is to switch to a Linux-based file system where all this stuff works, because it was designed in from the start.  I'd also script it.

---


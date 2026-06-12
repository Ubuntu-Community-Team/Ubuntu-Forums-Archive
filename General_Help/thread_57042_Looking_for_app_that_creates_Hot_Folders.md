---
title: "Looking for app that creates Hot Folders"
date: 2005-08-15
forum: General Help
---

### Post by nverhaar on 2005-08-15
Hey guys, im a HUGE lover of Ubuntu, but I am needing to create "Hot" or otherwise known as "Drop" folders.

I need to create several folders that will be watched and automatically run a command when certain files are placed into these folders.

For example, there would be an FTP folder which automatically picks up any files saved into this folder and FTP's them to a remote site. Another folder would be watched to automatically downsample and resize images, and another would automatically create PDF's.

I have used a program called Queuemon in the past, but cannot seem to find anything like it for Ubuntu. Does anyone have any suggestions?

---

### Post by Sam on 2005-08-15
This feature sounds great, however I've never heard of any app doing this.

But you can create scripts in nautilus available with the right mouse button menu. This is useful for doing batch operations on multiple files.

Create a script in ~/.gnome2/nautilus-scripts/ like that:
```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	<command_to_run> $uri &
done
```
Don't forget to chmod +x the script.

---

### Post by nverhaar on 2005-08-15
I dont think thats gonna do what I need to do here...

I am running Ubuntu on several servers at a newspaper company and we desperately need to setup HOT folders that can automatically create PDF's and FTP them to our print sites. We would also use such an app for auto resizing and colour correction of images via the use of ImageMagick.

We have used a little tool called QueueMon in the past, which allows you to setup exactly what I am asking for, except I am unable to locate it anywhere now.

If anyone can help I would appreciate it!!

---

### Post by rmjokers on 2005-08-15
I dont know how to do this automatically, but you could set up a cron job that checks the folder every 5 minutes or something.  This isnt quite as immediate as the hot folder idea, but it would be easy to set up...

---

### Post by nverhaar on 2005-08-15
Hrmmm yeah I guess a frequent cron job would do the trick, but I would prefer something more instantaneous that will pickup files on the fly and run various commands.

A utility such as this would be SO helpful, and im sure alot of others could make use of it as well.

---

### Post by wmcbrine on 2005-08-15
I'm sorry, but this is an arcane functionality provided by an obscure Windows utility. You shouldn't expect to see it anywhere else.

But of course, it could be done. Hmm... would you settle for an icon you could drag things onto, that didn't also pretend to be a folder? What exactly is the workflow you're trying to replicate?

Come to think of it, there's something like this already in Gnome -- the Desktop folder. It's a regular directory, but as you create files in it, their contents are scanned, and they appear as icons on screen. It works almost instantaneously, with no noticeable impact on performance. Might want to check how that works. (It does lose sync once in a while, though.)

---

### Post by nverhaar on 2005-08-15
Ummm no... its not a Windows utility. QueueMon is a small linux app that we have running on an ancient Mandrake server here. Now we're moving alot of servers over to Ubuntu, so we need this sort of functionality, but im unable to track down this QueueMon utility ANYWHERE!!

These Ubuntu servers are strictly servers, and therefore have a minimal server install, which means no desktop use at all so your solution doesnt really fit.

Anyone else got any ideas?

---

### Post by lakcaj on 2005-08-15
Sounds like you want to look at either dnotify, or its replacement, inotify

---

### Post by nverhaar on 2005-08-16
dnotify seems PERFECT for what I need it to do...

Now I have to figure out how to script it all... GRRRR!

---

### Post by wmcbrine on 2005-08-16
[QUOTE=nverhaar]Ummm no... its not a Windows utility. QueueMon is a small linux app that we have running on an ancient Mandrake server here.[/QUOTE]
Why don't you just copy it over, then?

I googled QueueMon, and all I found was something for Windows. That's why I wrote that, sorry. (I still say it's arcane.)

---

### Post by nverhaar on 2005-08-21
After a little more investigating, it looks like QueueMon is a custom app created by the linux guru we used to employ.
QueueMon is actually alot more complicated than it needs to be, and DNOTIFY should be capable of taking its place and doing the job nicely.

Thanks guys!

---


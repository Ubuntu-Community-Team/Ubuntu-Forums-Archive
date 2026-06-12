---
title: "Sed script to move files based on filename"
date: 2015-06-16
forum: General Help
---

### Post by NoHesitation on 2015-06-16
Hi,

I have looked all over, and found some examples, but nothing that gets me all the way to what I need, so any help you guys could provide would be greatly appreciated as I am a complete noob with sed and regex.

I am trying to move TV show files from one folder to another, but there are some conditions.

I have folders for 11 shows right now, but more could be added in the future.  The directory that the shows download to looks something like this: /downloads/TV/ and under that directory would be like /show1/ /show2/ /show3/ etc..
Inside those show specific folders would be the video files for each show, and they are always named like this: Show.Name.S00E00.Episode.Title.ext

More often than not, the files are .mkv files, but not always, so I can't solely go on the extention.

I would like to move the files from their /downloads/TV/Show folder to another location. It would look like /other/directory/Show/Season 1/
The "Show" portion of the path would always be the same from /downloads/ and /other/, but I need the script to parse the filename, find the season, and figure out which season folder it needs to go into.  It would have to truncate the leading zero to find the correct season directory, if there is one, but not if the first digit is >0.

Finally, I would like the script to parse all 11 "Show" directories, and if it finds a file in any one of them, move it to the corresponding "Show" directory in the other location.  It is also possible that there are other non-video files in the folder, but they would always be very small, and I would prefer to ignore those if possible.  I have been mucking around with the sed command to get the information off the filename first, but am having trouble making it work for all shows, as there is no constant number of characters between the beginning of the show name, and where the "S00" starts.

---

### Post by TheFu on 2015-06-17
This is a great way to learn regex, but if you don't care about that, there must be hundreds of TV show management scripts like this already created. Search for "vegan mediacenter" for one such guide with a list of tools.

BTW, I wouldn't use sed for this, I'd want a fuller language like python, ruby, perl, to do it.  Plus there are many, many, many, many, special situations with those filenames. There will always be someone who doesn't follow any known standard. Just sayin'. Don't expect any solution to be 100%.

BTW - if you do want to learn regex - great!  Post what you have and folks can help.

---


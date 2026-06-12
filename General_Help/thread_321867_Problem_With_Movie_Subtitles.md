---
title: "Problem With Movie Subtitles"
date: 2006-12-19
forum: General Help
---

### Post by 2pacalypse on 2006-12-19
I have a rather wierd problem, my Subtitles arent working, Every time i play the movie, and activate the subtitles the dont appear even if they posses the same name as the movie itself.  I've tried all the Media players on the repo's but none of them quite work, they all run the movie without the subtitles, however there are anomolies on two of them, first of all in Xine it does show subtitles, sorta... it shows all sorts of signs such as # @ ! ' and so on rather then actual letter (this is probably a hebrew font problem, however the problem still presists after I installed ** ALL ** the fonts i could find on the repo's) and MPlayer does play the movie at all, he just gives me an output of  "Fatal Error: Error Opening/initializing the selected video_out (-vo) device." does any1 know how to activate subtitles?


Thanks in advance

---

### Post by 2pacalypse on 2006-12-20
ok, i  managed to make it work in VLC too, but I still get wierd signs... and I prefure to run the movie on my totem-xine or kaffine.... this is probably a font problem, ** but  ** I already have all the fonts installed, I can use hebrew in the entire system except the subs for some reason so can any1 please help?

p.s.
is there anyway to combine the srt subtitle to the Xvid movie?

---

### Post by andb on 2007-06-29
The problem with subtitles is usually with the code page. For example, if you download files in  Central European languages, they tend to be in the WINDOWS-1250 code page. For them to display properly, try using iconv. 
```
$iconv -f WINDOWS-1250 -c -t utf-8 original_sub_file_name.sub > new_sub_file_name.sub
```
You will have to change the format that you are converting from. The -c switch will drop any strange character that don't belong. It shouldn't be necessary, but its good to know about if you have some problems. iconv with the -l switch will show you all of the format possibilities. If you ask a knowledgeable windows user in your area they should be able to narrow it down to one or two most likely codepages. 

I use VLC to watch video. Just works great on everything. You can even drag the subtitle file into it if it's name is different. I'm setting up Freevo 1.6 at the moment (maybe I should try 1.7 vlc support) so now I'm looking for a way to get mplayer working too...

---


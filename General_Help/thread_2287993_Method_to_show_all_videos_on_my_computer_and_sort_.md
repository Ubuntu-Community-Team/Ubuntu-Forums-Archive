---
title: "Method to show all videos on my computer and sort them by video bitrate?"
date: 2015-07-23
forum: General Help
---

### Post by Rytron on 2015-07-23
Hi.

Is there a way(s) to recursively scan all videos on my computer and sort them by video bitrate (highest to lowest)?

---

### Post by papibe on 2015-07-23
Hi Rytron.

Media players like Kodi can scan a recursively for all sorts of media. However, most of them would sort by things like, year, genre, rating, etc.

I would write an script, and use 'mediainfo' (now on the default repos). [Here]("http://ubuntuforums.org/showthread.php?t=1941386&highlight=mediainfo")'s an example of getting the aspect radio of every movie. 

Hope it helps. Let us know if you need more help with that.
Regards.

---

### Post by Rytron on 2015-07-24
> **papibe said:**
> Hi Rytron.

Media players like Kodi can scan a recursively for all sorts of media. However, most of them would sort by things like, year, genre, rating, etc.

I would write an script, and use 'mediainfo' (now on the default repos). [Here]("http://ubuntuforums.org/showthread.php?t=1941386&highlight=mediainfo")'s an example of getting the aspect radio of every movie. 

Hope it helps. Let us know if you need more help with that.
Regards.

Hi papibe.

I tried this:
```
mediainfo *.mkv | awk '/Bit rate/{print $5}
```

The output was:
```
Variable
Kbps
Kbps
Variable
Kbps
Kbps
Variable
Kbps
Kbps
Variable
Kbps
Kbps
Variable
Kbps
Kbps
Variable
Kbps
```

---

### Post by papibe on 2015-07-24
Your case is a little more complicated than the example I linked.

On a regular video, there will be several matches for the string 'Bit rate'. In this example:
```
$ mediainfo LAS.s38.e04.mp4 | grep 'Bit rate'
Bit rate                                 : 330 Kbps
Bit rate mode                            : Constant
Bit rate                                 : 128 Kbps

```
You'll get the audio bit rate, and then the video mode, and actual video bit rate.

Fortunately, mediainfo has a way to just print one parameter using the --Inform option.

Here's a couple of examples:
```
$ mediainfo --Inform="Video;%BitRate%" LAS.s38.e04.mp4
330000

$ mediainfo --Inform="Video;%BitRate/String%" LAS.s38.e04.mp4
330 Kbps
```
I hope that points you in the right direction. Let us know how it goes.
Regards.

---

### Post by Rytron on 2015-07-25
@papibe

```
mediainfo --Inform="Video;%BitRate/String%" *.mkv
```

```
486 Kbps560 Kbps567 Kbps563 Kbps563 Kbps566 Kbps
```

Can it be made recursive?

I prefer the second option you created -- it's more human readable when in kbps. ;-)

---

### Post by papibe on 2015-07-25
'mediainfo' is not recursive. It is a simple command line tool.

You can build a script that search recursively and for each movie found display the bit rate.

For example:
```
#!/bin/bash
# Get video bit rates for all movies.

# Get movies in the current directory.
while read -r -d '' movie; do
    #bit_rate=$(mediainfo --Inform='Video;%BitRate/String%' "$movie")
    bit_rate=$(mediainfo --Inform='Video;%BitRate%' "$movie")
    echo "$bit_rate $movie"
done< <(find . -type f \( \
    -iname '*.avi' -o \
    -iname '*.f4v' -o \
    -iname '*.flv' -o \
    -iname '*.mkv' -o \
    -iname '*.mov' -o \
    -iname '*.mp4' -o \
    -iname '*.mpeg' -o \
    -iname '*.mpg' -o \
    -iname '*.wmv' \) \
    -print0)

```
The 'String' option is great, but it prints big numbers with spaces instead of commas (or dots) so it not very useful for sorting.

In order to sort the output, you just sort the output of the script using the '-n' option for numeric sort:
```
./get_movie_bitrates.sh | sort -n
```
Note the this could take a while if you have lots of movies.

Hope it helps. Let us know if that works for you.
Regards.

---

### Post by Rytron on 2015-07-26
@papibe

It works fine. Could I get the output in Kbps? For example, it showed '1127395' where in VLC it says that video's bitrate is 1127 Kbps.

Thanks.

---

### Post by mc4man on 2015-07-26
> **Rytron said:**
> @papibe

It works fine. Could I get the output in Kbps? For example, it showed '1127395' where in VLC it says that video's bitrate is 1127 Kbps.

Thanks.
Kbps is reported with the commented out command in script, you could use that one & comment out the current command, ie.
....
    bit_rate=$(mediainfo --Inform='Video;%BitRate/String%' "$movie")
    #bit_rate=$(mediainfo --Inform='Video;%BitRate%' "$movie")
...

But any vid less than 1000 Kbs will sort after those with 1000+ Kbps & also any really high bitrate vids that get reported in Mbps due to the space in Kbps reporting
(if there was no space that would resolve less than 1000 sorting after 1000+ but would not resolve Mbps sorted before Kbps.

You could try editing the script as above & see how it works out in your case..

---

### Post by Rytron on 2015-07-26
> **mc4man said:**
> Kbps is reported with the commented out command in script, you could use that one & comment out the current command, ie.
....
    bit_rate=$(mediainfo --Inform='Video;%BitRate/String%' "$movie")
    #bit_rate=$(mediainfo --Inform='Video;%BitRate%' "$movie")
...

But any vid less than 1000 Kbs will sort after those with 1000+ Kbps & also any really high bitrate vids that get reported in Mbps due to the space in Kbps reporting
(if there was no space that would resolve less than 1000 sorting after 1000+ but would not resolve Mbps sorted before Kbps.

You could try editing the script as above & see how it works out in your case..

Excellent!

I can also just divide by 1000 to get the number in kbps so no big deal.

Thanks again mc4man.

---

### Post by Rytron on 2015-07-26
Sorting is tidier when using papibe's original code in post #6.

---

### Post by papibe on 2015-07-26
The easiest solution I can think of is to print both formats. If you put the raw number first it would get sorted correctly. Then the human-readable would be immediately after, as a reference:
```
...
while read -r -d '' movie; do
    **br_num**=$(mediainfo --Inform='Video;%BitRate%' "$movie")
    **br_hum**=$(mediainfo --Inform='Video;%BitRate/String%' "$movie")
    echo "**$br_num** (**$br_hum**) $movie"
done ...

```
Hope it helps.
Regards.

---

### Post by Rytron on 2015-07-27
> **papibe said:**
> The easiest solution I can think of is to print both formats. If you put the raw number first it would get sorted correctly. Then the human-readable would be immediately after, as a reference:
```
...
while read -r -d '' movie; do
    **br_num**=$(mediainfo --Inform='Video;%BitRate%' "$movie")
    **br_hum**=$(mediainfo --Inform='Video;%BitRate/String%' "$movie")
    echo "**$br_num** (**$br_hum**) $movie"
done ...

```
Hope it helps.
Regards.

Excellent stuff, papibe.

So your full code is:

```
#!/bin/bash
# Get video bit rates for all movies.

# Get movies in the current directory.
while read -r -d '' movie; do
 br_num=$(mediainfo --Inform='Video;%BitRate%' "$movie")
 br_hum=$(mediainfo --Inform='Video;%BitRate/String%' "$movie")
echo "$br_num ($br_hum) $movie"
done< <(find . -type f \( \
    -iname '*.avi' -o \
    -iname '*.f4v' -o \
    -iname '*.flv' -o \
    -iname '*.mkv' -o \
    -iname '*.mov' -o \
    -iname '*.mp4' -o \
    -iname '*.mpeg' -o \
    -iname '*.mpg' -o \
    -iname '*.webm' -o \
    -iname '*.wmv' \) \
    -print0)
```

I added in 'webm'. ;)

---

### Post by mc4man on 2015-07-27
Just for the heck of it did file an upstream issue about the space in Kbps which is also seen in the gui. We'll see if there is some fix there down the road
(though the bps is better for your use..

---

### Post by mc4man on 2015-07-27
> **mc4man said:**
> Just for the heck of it did file an upstream issue about the space in Kbps which is also seen in the gui. We'll see if there is some fix there down the road
(though the bps is better for your use..
Well they claim the space is a thousand separator & can be removed with option of (red
--Inform="Video;%BitRate/String%" [COLOR="#FF0000"]--Language=" Config_Text_ThousandsSeparator;"[/COLOR] 
Probably works on windows but not here in Ubuntu

But this does remove the space - --Language=raw

---

### Post by Rytron on 2015-07-27
> **mc4man said:**
> Well they claim the space is a thousand separator & can be removed with option of (red
--Inform="Video;%BitRate/String%" [COLOR="#FF0000"]--Language=" Config_Text_ThousandsSeparator;"[/COLOR] 
Probably works on windows but not here in Ubuntu

But this does remove the space - --Language=raw

Thanks for the info.

---

### Post by Rytron on 2015-07-30
I also added this line to bash file:

```
-iname '*.ogv' -o \
```

---


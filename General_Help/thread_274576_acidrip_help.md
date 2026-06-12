---
title: "acidrip help"
date: 2006-10-10
forum: General Help
---

### Post by ntbutler on 2006-10-10
hey guys
i have a music vid dvd, and i want to make separate avi or mpg files for each song (each song in a new chapter).
i have tried dvdrip and acidrip, and in both cases all i can get is the first chapter.
any ideas?

---

### Post by mssever on 2006-10-10
This works for me:

Copy the contents of the DVD's video_ts folder to your hard drive (you don't need to rip DVDs) and open the first video file (the name begins with vts) in avidemux, allowing it to index and append when it asks. Then, find the song boundries and delete the rest. Save the file. Repeat.

---

### Post by ntbutler on 2006-10-10
thanks mate, i will give it a go.

---

### Post by ntbutler on 2006-10-13
Heya.
i have tried copying the VIDEO_TS folder and opening that in avidemux, but that gets the title screen menu, and thats it, no other chapters.
I tried the way they said on their website, by using the command "mplayer dvd://1 -dumpstream -dumpfile rippeddvd.vob", but that only put the first song on, same result as using dvdrip or acidrip... do you know what i am doing wrong, or is it just the type of dvd?

---

### Post by mssever on 2006-10-13
My experience with DVDs is limited, but perhaps you opened the wrong file? Also, there aren't different files for different chapters. You'll have to manually find the chapter divisions in Avidemux.

---


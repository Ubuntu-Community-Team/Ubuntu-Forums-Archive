---
title: "Store awk result in variable issue"
date: 2006-08-11
forum: General Help
---

### Post by stevea1210 on 2006-08-11
I am writing a script for video on demand using vlc.  I am having a problem with an AWK statement in it.  I am trying to get the results of an AWK statement stored in a variable.

I have the full path to a movie stored in variable $MOVIENAME
I want to remove the path and the extension from that, leaving only the name of the movie, and store that in a variable.

The AWK statement I'm using is:
$MOVIENAME|awk -F/ '{print $NF}'|awk -F. '{print $1}'
(First AWK statement removes the path, second removes the extension)

If I do:
echo $MOVIENAME|awk -F/ '{print $NF}'|awk -F. '{print $1}'
I get the results I want in the terminal.

To store in a variable I have tried:
TEST=`$MOVIENAME|awk -F/ '{print $NF}'|awk -F. '{print $1}'`
and
TEST=$($MOVIENAME|awk -F/ '{print $NF}'|awk -F. '{print $1}')

Neither are working.  When I run the script, I get the below output for a few lines
./vlc2.sh: line 33: /netshares/movies/fantastic4/fantastic-4.avi: cannot execute binary file

Then the entire terminal turns into "binary looking" characters. I have to close the terminal. Both of the above versions give the same result.  I have attache a screenshot of how the terminal looks.

Can anyone assist in this?  How should that line look to get the variable to store the result of the AWK statement?

---

### Post by simonn on 2006-08-11
TEST=`**echo** $MOVIENAME|awk -F/ '{print $NF}'|awk -F. '{print $1}'`

---

### Post by stevea1210 on 2006-08-11
Thanks Simonn.  As soon as I read your reply, I felt a little, well, dumb.  I need to stop working on this projeect and go to bed ;).  BTW, it worked of course.

thanks again :)

---


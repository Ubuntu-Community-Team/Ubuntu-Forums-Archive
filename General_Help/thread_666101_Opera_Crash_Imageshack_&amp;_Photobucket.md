---
title: "Opera Crash: Imageshack &amp; Photobucket"
date: 2008-01-13
forum: General Help
---

### Post by vahnx on 2008-01-13
When I upload an image on Photobucket or Imageshack in Opera 9.5 on Ubuntu 7.10, the browser crashes. I'd post an error log but I couldn't find one in the /home/name/.opera

---

### Post by SOULRiDER on 2008-01-13
Try running opera from a terminal and see if it prints any errors when it crashes. Post the output here.

---

### Post by vahnx on 2008-01-13
Oh yeah, I was Googling on the error and couldn't find anything:

(operapluginwrapper:6236): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
The program '<unknown>' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 60638 error_code 3 request_code 12 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by SOULRiDER on 2008-01-13
I find thats odd since Opera, AFAIK, uses QT. Opera 9.5 seems to be the beta since the site mentions 9.25 to be the latest stable release. I recommend you stick with 9.25 unless you need 9.5 for some of its features. There is also 9.5b.

Try with any of those versions and see if Opera still crashes, im guessing they fixed it quickly since its a rather major bug.

Good luck and post results :)

---

### Post by vahnx on 2008-01-13
I switched from 9.25 to 9.5 because I was having issues with flash. The only problem with Opera 9.5 I find is those image uploading sites, I can use Firefox for that I guess =D

---

### Post by SOULRiDER on 2008-01-13
Good thing things are sorted out now. Could you please mark the thread as solved?
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by vahnx on 2008-01-13
It's not solved. It still crashes. Say if someone had the same issue, they could continue posting here building on what I already wrote. But I chose an alternative method, I chose to use Firefox to upload my images.

---

### Post by kansei on 2008-01-16
When people link me to photos on those sites (also webshots.. ugh what an awful site) it often crashes Opera 9.5.

I think it's because they use flash ads. Flash crashes Opera for me like 30x a day. I know it's beta but it's the only 'out of the box' Opera version that works with Flash 9 right now.

---


---
title: "EPS to PDF tools..."
date: 2014-05-13
forum: General Help
---

### Post by eslavko on 2014-05-13
Hello....
I have problem with conversion from EPS to PDF. I tried epstopdf, inkscape, ghostscript but all fail with error. Seems that my eps is corrupted, but on the other hands in windowsXP 5dtopdf convert that same file without problem. But I want to get out of that wXP... Is there some other tools?

here is sample file:
[https://dl.dropboxusercontent.com/u/73877244/sch.eps](https://dl.dropboxusercontent.com/u/73877244/sch.eps)

thanks.

---

### Post by slickymaster on 2014-05-13
Convert is a part of the Imagemagick package, which is in the repo's.
[http://www.imagemagick.org/script/command-line-tools.php]("http://www.imagemagick.org/script/co...line-tools.php")

---

### Post by eslavko on 2014-05-13
I try with display but get error

[I]slavko@ePodstresnik:~/xx$ display sch.eps
Error: /rangecheck in -file-
Operand stack:
   0   1   0
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1910   1   3   %oparray_pop   1909   1   3   %oparray_pop   --nostringval--   1893   1   3   %oparray_pop   1787   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push
Dictionary stack:
   --dict:1166/1684(ro)(G)--   --dict:0/20(G)--   --dict:146/200(L)--
Current allocation mode is local
Last OS error: 2
Current file position is 564900
GPL Ghostscript 9.05: Unrecoverable error, exit code 1
Error: /rangecheck in -file-
Operand stack:
   0   1   0
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1910   1   3   %oparray_pop   1909   1   3   %oparray_pop   --nostringval--   1893   1   3   %oparray_pop   1787   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push
Dictionary stack:
   --dict:1166/1684(ro)(G)--   --dict:0/20(G)--   --dict:146/200(L)--
Current allocation mode is local
Last OS error: 2
Current file position is 564900
GPL Ghostscript 9.05: Unrecoverable error, exit code 1
display: Postscript delegate failed `sch.eps':  @ error/ps.c/ReadPSImage/806.
[/I]

---

### Post by eslavko on 2014-08-25
the input file was corrupted...

---


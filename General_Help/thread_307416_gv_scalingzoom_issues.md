---
title: "gv scaling/zoom issues"
date: 2006-11-26
forum: General Help
---

### Post by kanawa1 on 2006-11-26
Hi,

I am having trouble using gv to scale or zoom
into a .pdf file. This happened after I upgraded to Edgy.

Scaling/zoom works properly if I open gv on
the command line and the file is in the same
directory or a subdirectory of the directory from which gv was opened. Eg if gv is opened
from /home/parrot/docs then scaling works properly with a file in /home/parrot/docs/ubuntu/ but not with files in
/home/parrot or files in /tmp

Opening gv from any other directory causes problems when scaling/zooming with an 
invalidfileaccess error from gs - see below

It used to work fine in Dapper. Upgrading to
gs-gpl version 8.50 made no difference.

Thanks
Manmatha

------------Error Message ----
ERROR: /invalidfileaccess in --file--ESP Ghostscript 815.02: Unrecoverable error, exit code 1

Operand stack:
   (../help.pdf)   (r)
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1   3   %oparray_pop   1   3   %oparray_pop   1   3   %oparray_pop   1   3   %oparray_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1122/1686(ro)(G)--   --dict:0/20(G)--   --dict:85/200(L)--   --dict:104/127(ro)(G)--   --dict:241/347(G)--
Current allocation mode is local

---

### Post by kanawa1 on 2006-11-27
Fixed the problem by upgrading to debian package gv 3.6.2.2
(the ubuntu/kubuntu version doesn't seem to be available yet).


Manmatha

---


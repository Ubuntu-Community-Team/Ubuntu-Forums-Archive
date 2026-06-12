---
title: "Spliting large files under Linux using RAR"
date: 2005-07-21
forum: General Help
---

### Post by Holdem on 2005-07-21
Does anyone know how I can split large files in to RAR format so they can be easily emailed to a Windows user? Under Windows you can use WinRAR and the GUI wizard asks what size to split them to. I found this [http://www.rarlab.com/download.htm](http://www.rarlab.com/download.htm) version for Linux and it's command line but their are no instructions, anyone know how it's done? Or if there is another way to split down files under Linux that can then be opened on multiple platforms?

---

### Post by poptones on 2005-07-21
If you type "man rar" do you not get instructions on use? Try rar --help and that should give you usage. Here is what I get:

RAR 3.40   Copyright (c) 1993-2004 Alexander Roshal   8 Sep 2004
Shareware version         Type RAR -? for help

Usage:     rar <command> -<switch 1> -<switch N> <archive> <files...>
               <@listfiles...> <path_to_extract\>

<Commands>
  a             Add files to archive
  c             Add archive comment
  cf            Add files comment
  cw            Write archive comment to file
  d             Delete files from archive
  e             Extract files to current directory
  f             Freshen files in archive
  i[par]=<str>  Find string in archives
  k             Lock archive
  l[t,b]        List archive [technical, bare]
  m[f]          Move to archive [files only]
  p             Print file to stdout
  r             Repair archive
  rc            Reconstruct missing volumes
  rn            Rename archived files
  rr[N]         Add data recovery record
  rv[N]         Create recovery volumes
  s[name|-]     Convert archive to or from SFX
  t             Test archive files
  u             Update files in archive
  v[t,b]        Verbosely list archive [technical,bare]
  x             Extract files with full path

<Switches>
  -             Stop switches scanning
  ad            Append archive name to destination path
  ag[format]    Generate archive name using the current date
  ap<path>      Set path inside archive
  as            Synchronize archive contents
  av            Put authenticity verification (registered versions only)
  av-           Disable authenticity verification check
  c-            Disable comments show
  cfg-          Disable read configuration
  cl            Convert names to lower case
  cu            Convert names to upper case
  df            Delete files after archiving
  dh            Open shared files
  ds            Disable name sort for solid archive
  e<attr>       Set file exclude attributes
  ed            Do not add empty directories
  en            Do not put 'end of archive' block
  ep            Exclude paths from names
  ep1           Exclude base directory from names
  ep3           Expand paths to full including the drive letter
  f             Freshen files
  hp[password]  Encrypt both file data and headers
  idp           Disable percentage display
  ierr          Send all messages to stderr
  ilog[name]    Log errors to file (registered versions only)
  inul          Disable all messages
  isnd          Enable sound
  k             Lock archive
  kb            Keep broken extracted files
  m<0..5>       Set compression level (0-store...3-default...5-maximal)
  mc<par>       Set advanced compression parameters
  md<size>      Dictionary size in KB (64,128,256,512,1024,2048,4096 or A-G)
  ms[ext;ext]   Specify file types to store
  o+            Overwrite existing files
  o-            Do not overwrite existing files
  ol            Save symbolic links as the link instead of the file
  ow            Save or restore file owner and group
  p[password]   Set password
  p-            Do not query password
  r             Recurse subdirectories
  r0            Recurse subdirectories for wildcard names only
  ri<P>[:<S>]   Set priority (0-default,1-min..15-max) and sleep time in ms
  rr[N]         Add data recovery record
  rv[N]         Create recovery volumes
  s[<N>,v[-],e] Create solid archive
  s-            Disable solid archiving
  sfx[name]     Create SFX archive
  si[name]      Read data from standard input (stdin)
  t             Test files after archiving
  ta<date>      Process files modified after <date> in YYYYMMDDHHMMSS format
  tb<date>      Process files modified before <date> in YYYYMMDDHHMMSS format
  tk            Keep original archive time
  tl            Set archive time to latest file
  tn<time>      Process files newer than <time>
  to<time>      Process files older than <time>
  ts<m,c,a>[N]  Save or restore file time (modification, creation, access)
  u             Update files
  v             Create volumes with size autodetection or list all volumes
  v<size>[k,b]  Create volumes with size=<size>*1000 [*1024, *1]
  ver[n]        File version control
  vn            Use the old style volume naming scheme
  vp            Pause before each volume
  w<path>       Assign work directory
  x<file>       Exclude specified file
  x@            Read file names to exclude from stdin
  x@<list>      Exclude files in specified list file
  y             Assume Yes on all queries
  z<file>       Read archive comment from file

Anyway, to make it split to 1 MB volumes you would use something like 

rar a -v1024k file outfile

Change 1024k to whatever volume size you like, but for email I wouldn't suggest it unless you're both using gmail or something.

---

### Post by Holdem on 2005-07-21
Thanks for that.
I'm new to Linux and had forgotten about the 'man' command.
Thanks for the last bit I'll give that a go.

---

### Post by poptones on 2005-07-21
Hey, I'm on your side. I think the GUI wizard in gnome should be seriously updated with some preference panels so you dont have to use the command line just to do common tasks like splitting or encrypting/decrypting... but I'm not sure how to do that  myself.

---


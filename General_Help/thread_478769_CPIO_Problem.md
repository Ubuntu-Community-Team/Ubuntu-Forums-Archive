---
title: "CPIO Problem"
date: 2007-06-19
forum: General Help
---

### Post by adamorjames on 2007-06-19
For some reason it says that the CPIO I inputed is wrong. Can someone figure out why? Have the commands changed? Here it is-
```

find . -depth -print0 | cpio &#8211;null &#8211;sparse -pvd /mnt/newhome/

```
If the commands have changed then what would be the equivalent to the above?

---

### Post by avik on 2007-06-19
You got that from the Ubuntu blog, huh?

I had the same problem.  Precede both null and spares with **two** hyphens instead of one.  That should do it.

---

### Post by adamorjames on 2007-06-19
Ya, I got it from a blog. So, I tried-
```

find . -depth -print0 | cpio &#8211;&#8211;null &#8211;&#8211;sparse -pvd /mnt/newhome/

```
like you said but it didn't work. The error it gives is -
```

cpio: You must specify one of -oipt options.
Try `cpio --help' or `cpio --usage' for more information.

```
When I type cpio --help it gives commands.
Here's what it gives-
```

Usage: cpio [OPTION...] [destination-directory]
GNU `cpio' copies files to and from archives

Examples:
  # Copy files named in name-list to the archive
  cpio -o < name-list [> archive]
  # Extract files from the archive
  cpio -i [< archive]
  # Copy files named in name-list to destination-directory
  cpio -p destination-directory < name-list

 Main operation mode:
  -i, --extract              Extract files from an archive (run in copy-in
                             mode)
  -o, --create               Create the archive (run in copy-out mode)
  -p, --pass-through         Run in copy-pass mode
  -t, --list                 Print a table of contents of the input

 Operation modifiers valid in any mode:

      --block-size=BLOCK-SIZE   Set the I/O block size to BLOCK-SIZE * 512
                             bytes
  -B                         Set the I/O block size to 5120 bytes
  -c                         Use the old portable (ASCII) archive format
  -C, --io-size=NUMBER       Set the I/O block size to the given NUMBER of
                             bytes
      --force-local          Archive file is local, even if its name contains
                             colons
  -f, --nonmatching          Only copy files that do not match any of the given
                             patterns
  -F, --file=[[USER@]HOST:]FILE-NAME
                             Use this FILE-NAME instead of standard input or
                             output. Optional USER and HOST specify the user
                             and host names in case of a remote archive
  -H, --format=FORMAT        Use given archive FORMAT
  -M, --message=STRING       Print STRING when the end of a volume of the
                             backup media is reached
  -n, --numeric-uid-gid      In the verbose table of contents listing, show
                             numeric UID and GID
      --quiet                Do not print the number of blocks copied
      --rsh-command=COMMAND  Use remote COMMAND instead of rsh
  -v, --verbose              Verbosely list the files processed
  -V, --dot                  Print a "." for each file processed
  -W, --warning=FLAG         Control warning display. Currently FLAG is one of
                             'none', 'truncate', 'all'. Multiple options
                             accumulate.

 Operation modifiers valid only in copy-in mode:

  -b, --swap                 Swap both halfwords of words and bytes of
                             halfwords in the data. Equivalent to -sS
  -E, --pattern-file=FILE    In copy-in mode, read additional patterns
                             specifying filenames to extract or list from FILE
      --no-absolute-filenames   Create all files relative to the current
                             directory
      --only-verify-crc      When reading a CRC format archive in copy-in mode,
                             only verify the CRC's of each file in the archive,
                             don't actually extract the files
  -r, --rename               Interactively rename files
  -s, --swap-bytes           Swap the bytes of each halfword in the files
  -S, --swap-halfwords       Swap the halfwords of each word (4 bytes) in the
                             files
      --to-stdout            Extract files to standard output

 Operation modifiers valid only in copy-out mode:

  -A, --append               Append to an existing archive.
  -O [[USER@]HOST:]FILE-NAME Archive filename to use instead of standard
                             output. Optional USER and HOST specify the user
                             and host names in case of a remote archive

 Operation modifiers valid only in copy-pass mode:

  -l, --link                 Link files instead of copying them, when
                             possible

 Operation modifiers valid for copy-out and copy-pass modes:

  -0, --null                 A list of filenames is terminated by a null
                             character instead of a newline
  -a, --reset-access-time    Reset the access times of files after reading them

  -I [[USER@]HOST:]FILE-NAME Archive filename to use instead of standard input.
                             Optional USER and HOST specify the user and host
                             names in case of a remote archive
  -L, --dereference          Dereference  symbolic  links  (copy  the files
                             that they point to instead of copying the links).
  -R, --owner=[USER][:.][GROUP]   Set the ownership of all files created to the
                             specified USER and/or GROUP
      --sparse               Write files with large blocks of zeros as sparse
                             files

 Operation modifiers valid for copy-in and copy-pass modes:

  -d, --make-directories     Create leading directories where needed
  -m, --preserve-modification-time
                             Retain previous file modification times when
                             creating files
      --no-preserve-owner    Do not change the ownership of the files
  -u, --unconditional        Replace all files unconditionally

 Informative options:

  -?, --help                 Give this help list
      --license              Print license and exit
      --usage                Give a short usage message
      --version              Print program version

Mandatory or optional arguments to long options are also mandatory or optional
for any corresponding short options.


```

---

### Post by adamorjames on 2007-06-19
I fixed it. It was two hyphen problems. The double hyphen was the first hyphen problem so thanks avik for helping me fix that part. The other was that some of the hyphens were not hyphens. Now that that's fixed it's time to move on to the next problem that comes after syntax.... permission denied. See ya.

---

### Post by avik on 2007-06-19
I understand what the problem is, but I don't think it should be there.

Neverthless, prefix the cpio command with sudo.

---

### Post by adamorjames on 2007-06-19
Couldn't fix it with sudo. Had to boot up as single/root user. After that I got the /home directory on a separate partition.

---

### Post by avik on 2007-06-19
Well, good to hear you got it working.  Putting my data on a separate hard drive has saved me a couple of times!  It's great.

---

### Post by adamorjames on 2007-06-19
Yeah, I think it'll be great to have it  separate. My next goal is to figure out how to run more than 1 distro. I mostly got it figured out, it's just the GRUB part that has got me a bit stuck. Also it's sad that some distros don't give the user a choice of wether to install a bootloader or not. Got to read up on any unknown distro, just in case.

---

### Post by westdale on 2008-05-14
I have been doing this same operation to move /home to a separate partition
Forced on me by some bad blocks - so I have split my main partition around them. To take advantage of having to do this, I am moving /home as well.

However, cpio ( with a sudo in front ) is not carrying over owner/group etc
On restart, Gnome protests at login because it can't do some things.

I have restored into my (now rather small) part partition - does anyone have an idea about ownership and permissions in cpio ?
I find the different text in the info page very confusing in the sudo case:

`--no-preserve-owner'
     Do not change the ownership of the files; leave them owned by the
     user extracting them. 

If I extract (as user gw, sudo) from user peter, then setting owner to gw IS changing the owner!

--- later ---
took a gamble and  chowned/chgrpd -R gw ~  
this rejected a change to the network file daemon (good!) but otherwise seems to have got me up and working in the new partition (including network devices over wireless!)

I hate hacking blindly and would dearly like someone knowledgeable to tell me about sudo cpio ! :-)

---


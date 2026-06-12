---
title: "Has anyone compiled ncmpc-svn?"
date: 2006-09-29
forum: General Help
---

### Post by grte on 2006-09-29
If you have, I'm having a problem and would be grateful if you could give me any help.

I downloaded it through subversion, then ran the commands ./autogen.sh, make, make install, as the instructions instruced me to.  And it configures and compiles fine.  But when I try to make install, I get this:

```
Making install in src
make[1]: Entering directory `/home/avatar/ncmpc/src'
make[2]: Entering directory `/home/avatar/ncmpc/src'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'ncmpc' '/usr/local/bin/ncmpc'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/avatar/ncmpc/src'
make[1]: Leaving directory `/home/avatar/ncmpc/src'
Making install in doc
make[1]: Entering directory `/home/avatar/ncmpc/doc'
make[2]: Entering directory `/home/avatar/ncmpc/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/doc/ncmpc" || mkdir -p -- "/usr/local/share/doc/ncmpc" /usr/bin/install -c -m 644 'config.sample' '/usr/local/share/doc/ncmpc/config.sample'
 /usr/bin/install -c -m 644 'keys.sample' '/usr/local/share/doc/ncmpc/keys.sample'
 /usr/bin/install -c -m 644 'ncmpc.lirc' '/usr/local/share/doc/ncmpc/ncmpc.lirc'test -z "/usr/local/man/man1" || mkdir -p -- "/usr/local/man/man1"
 /usr/bin/install -c -m 644 './ncmpc.1' '/usr/local/man/man1/ncmpc.1'
make[2]: Leaving directory `/home/avatar/ncmpc/doc'
make[1]: Leaving directory `/home/avatar/ncmpc/doc'
Making install in po
make[1]: Entering directory `/home/avatar/ncmpc/po'
if test -r ".././mkinstalldirs"; then \
          .././mkinstalldirs /usr/local/share; \
        else \
          /bin/sh ../mkinstalldirs /usr/local/share; \
        fi
/bin/sh: ../mkinstalldirs: No such file or directory
make[1]: *** [install-data-yes] Error 127
make[1]: Leaving directory `/home/avatar/ncmpc/po'
make: *** [install-recursive] Error 1
```

Any ideas why?

---

### Post by grte on 2006-10-01
Okay, I've figured it out.  For anyone who is having or may have the same issue, here's what I did:

Copy the following text into a file named mkinstalldirs and save it into the ncmpc/ directory:

```
#! /bin/sh
# mkinstalldirs --- make directory hierarchy
# Author: Noah Friedman <friedman@prep.ai.mit.edu>
# Created: 1993-05-16
# Public domain

errstatus=0
dirmode=""

usage="\
Usage: mkinstalldirs [-h] [--help] [-m mode] dir ..."

# process command line arguments
while test $# -gt 0 ; do
   case "${1}" in
     -h | --help | --h* )			# -h for help
	echo "${usage}" 1>&2; exit 0 ;;
     -m )					# -m PERM arg
	shift
	test $# -eq 0 && { echo "${usage}" 1>&2; exit 1; }
	dirmode="${1}"
	shift ;;
     -- ) shift; break ;;			# stop option processing
     -* ) echo "${usage}" 1>&2; exit 1 ;;	# unknown option
     * )  break ;;				# first non-opt arg
   esac
done

for file
do
  if test -d "$file"; then
    shift
  else
    break
  fi
done

case $# in
0) exit 0 ;;
esac

case $dirmode in
'')
  if mkdir -p -- . 2>/dev/null; then
    echo "mkdir -p -- $*"
    exec mkdir -p -- "$@"
  fi ;;
*)
  if mkdir -m "$dirmode" -p -- . 2>/dev/null; then
    echo "mkdir -m $dirmode -p -- $*"
    exec mkdir -m "$dirmode" -p -- "$@"
  fi ;;
esac

for file
do
   set fnord `echo ":$file" | sed -ne 's/^:\//#/;s/^://;s/\// /g;s/^#/\//;p'`
   shift

   pathcomp=
   for d
   do
     pathcomp="$pathcomp$d"
     case "$pathcomp" in
       -* ) pathcomp=./$pathcomp ;;
     esac

     if test ! -d "$pathcomp"; then
	echo "mkdir $pathcomp"

	mkdir "$pathcomp" || lasterr=$?

	if test ! -d "$pathcomp"; then
	  errstatus=$lasterr
	else
	  if test ! -z "$dirmode"; then
	     echo "chmod $dirmode $pathcomp"

	     lasterr=""
	     chmod "$dirmode" "$pathcomp" || lasterr=$?

	     if test ! -z "$lasterr"; then
	       errstatus=$lasterr
	     fi
	  fi
	fi
     fi

     pathcomp="$pathcomp/"
   done
done

exit $errstatus

# Local Variables:
# mode: shell-script
# sh-indentation: 3
# End:
# mkinstalldirs ends here
```

It should now install fine (though checkinstall didn't work, make install worked fine.)

---

### Post by JMO707 on 2006-10-26
Thanks. A lot ^^

---


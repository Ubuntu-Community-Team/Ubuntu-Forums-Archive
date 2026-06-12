---
title: "[SOLVED] HTH do you make Firefox run the -ProfileManager option?!?"
date: 2007-11-20
forum: General Help
---

### Post by jdackle on 2007-11-20
This is one of them situations I almost believe I am using Windows again... ](*,)

So, how the heck DO you run firefox with the profile manager?
issuing:```
firefox -ProfileManager
``` simply IGNORES the option and happily goes directly to the default profile... ](*,)
BTW, this DID work before ... I upgraded to Gutsy from Dapper...

Looking at run-mozilla.sh:
```
##########################################################################
##
## Command line arg defaults
##
moz_debug=0
moz_debugger=""
#
##
## Parse the command line
##
while [ $# -gt 0 ]
do
  case $1 in
    -g | --debug)
      moz_debug=1
      shift
      ;;
    -d | --debugger)
      moz_debugger=$2;
      if [ "${moz_debugger}" != "" ]; then
	shift 2
      else
        echo "-d requires an argument"
        exit 1
      fi
      ;;
    *)
      break;
      ;;

  esac
done
```

So, erm, if I understood correctly... any option other than de debugging ones is IGNORED?! :confused: ](*,)

WTH?!?


Heck, I must be doing something really stupyd here... or else... ](*,)


Help anyone?

---

### Post by bettlebrox on 2007-11-20
It's a bug in FIrefox on Ubuntu, see the link below for more details (and possible workarounds):

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/31746](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/31746)

---

### Post by jdackle on 2007-11-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/31746](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/31746) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thanks a lot bettlebrox! :)

Yes, it's a bug and yes the workarounds mentioned in your link work. So, as there is a sollution to the problem, I'll mark this as "solved" and hope the bug itself gets fixed too. :-)

Cheers!

---

### Post by daengbo on 2007-11-20
You can also just call Firefox directly
/usr/lib/firefox/firefox -ProfileManager

---


---
title: "want to select output of pstree/grep highlight"
date: 2006-11-22
forum: General Help
---

### Post by CareySchug on 2006-11-22
In a pipeline in a shell script, I want to search the parents of my running pid to make sure I don't run something recursively (mostly a script command).   In solaris I do a 'ps -opid' to get my pid, then 'ptree #' with that pid number and it shows a tree only of that pid.

The pstree equivalent in Linux, as far as i can tell, doesn't have a way to limit it to one pid's tree.  I can say pstree -hlapA and get a complete tree, similar to ptree, with my branch highlighted, so if I an grep on 'highlighted text' I would be actually BETTER off than in Solaris, as I could do it all in one step.  However, I can't find anything in grep to do that, maybe throug ignorance or maybe it isn't there.  Or is there some other command to select just the highlighted output in a pipe?

I think could search for myself (the end of the branch, cutting off everything after), then search back for the base of the branch (cutting off  everything before), but that is difficult (at least for me) and would take me a while to figure out.

In the examples below, the original output succesive child entries are further to the right, but that doesn't matter for how I would parse in the shell script.

here is a ptree output:
ctsult5a/export/home/carey: ptree 1866
147   /usr/sbin/inetd -s
  1759  in.telnetd
    1761  -ksh
      1822  /usr/bin/ksh cts log
        1864  script ./console.061122190324
          1865  script ./console.061122190324
            1866  sh -i
              2002  ptree 1866

and here is an excerpt of a pstree output:
...
  |-gnome-settings-,5003 --oaf-activate-iid=OAFIID
  |   `-{gnome-settings-},5005
  |-gnome-terminal,9520
  |   |-bash,9522
  |   |   |-script,13811 test
  |   |   |   `-script,13812 test
  |   |   |       `-bash,13813 -i
  |   |   |           `-script,13907 temp2
  |   |   |               `-script,13908 temp2
  |   |   |                   `-bash,13909 -i
  |   |   |                       `-script,13932 temp3
  |   |   |                           `-script,13933 temp3
  |   |   |                               `-bash,13934 -i
  |   |   |                                   `-pstree,14606 -hlapA
  |   |   |-winevdm.exe,10200 --app-name I:\sys\MINES.exe MINES
  |   |   |   |-explorer.exe,10213 /desktop
  |   |   |   |   `-{explorer.exe},10214
...

---

### Post by jonathanwalshuk on 2008-01-18
Whats wrong with :

~$ pstree -lpA <pid#>

e.g.
~$ pstree -hp 13879
run-mozilla.sh(13879)&#9472;&#9472;&#9472;firefox-bin(13883)&#9472;&#9516;&#9472;{firefox-bin}(13884)
                                                                           &#9500;&#9472;{firefox-bin}(13885)
                                                                           &#9500;&#9472;{firefox-bin}(13887)
                                                                           &#9500;&#9472;{firefox-bin}(13888)
                                                                           &#9500;&#9472;{firefox-bin}(13889)
                                                                           &#9492;&#9472;{firefox-bin}(13894)

---

### Post by CareySchug on 2008-01-18
That only displays as far back as the last shell.  My immediate purpose is to determine if the process I am running in has a "script" command running.  But script starts a new shell, so the option specified doesn't show anything before the shell, specifically does not show the script command.  The ultimate purpose is to guarantee documentation is collected on what is being done.  This is serious business work.  And ONLY one copy, to save disk space (and not have to search a bazillion logs later on).  I need to show my parents all the way back to the original log on or before.  In Solaris, I can su to another id (e.g. root), then su back to my own and on to a third, and each of them will know the very first logon started a script and not start new ones.  Linux has a lot of nice features, but not hard core business oriented stuff.

---


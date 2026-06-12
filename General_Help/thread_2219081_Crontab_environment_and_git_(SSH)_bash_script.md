---
title: "Crontab environment and git (SSH) bash script"
date: 2014-04-22
forum: General Help
---

### Post by andrew102 on 2014-04-22
Hi,

I am trying to get a bash script that runs both a git pull and git push command. The problem is that git doesn't allow you to explicitly specify a SSH key, instead i relies on ssh-agent or something.

So I went down the path of installing a module named "keychain"

Supposedly this is the solution to get the crontab environment set up to use the ssh keys.

[B]The problem I'm having is invoking keychain, I'll give some code here to show my basic setup.

[/B]
For bash.rc, I have

```
if [ -x /usr/bin/keychain ]; then
  /usr/bin/keychain --quiet /home/username/.ssh/id_rsa
fi
```


My parent script is located in /opt/repos/some_folder, it calls some other scripts, one of which is used for git pull, add, commit and another for git push.

So they look something like

```
cd /opt/repos/some_folder/the_folder_from_github
~/.keychain/hostname-sh
git pull --progress >> log_file.log
.....
```

```
cd /opt/repos/some_folder/the_folder_from_github
~/.keychain/hostname-sh
git push --progress >> log_file.log
.....
```


( BTW, so far I have found git to be useless at piping out to log files )

---

### Post by papibe on 2014-04-22
Hi andrew102.

Have you tried using the environment variable 'GIT_SSH'? Take a look at this example: [How to specify an ssh-key file with the Git command]("http://alvinabad.wordpress.com/2013/03/23/how-to-specify-an-ssh-key-file-with-the-git-command/").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by andrew102 on 2014-04-23
> **papibe said:**
> Hi andrew102.

Have you tried using the environment variable 'GIT_SSH'? Take a look at this example: [How to specify an ssh-key file with the Git command]("http://alvinabad.wordpress.com/2013/03/23/how-to-specify-an-ssh-key-file-with-the-git-command/").

Hope it helps. Let us know how it goes.
Regards.

Ok so tried that and got these errors:

/opt/rxxx/xx/git.sh: line 20: chmod: command not found
/opt/rxxx/xx/git.sh: line 28: git: command not found
/opt/rxxx/xx/git.sh: line 1: rm: command not found


Would this be a permissions issue or just crontab ?

---

### Post by andrew102 on 2014-04-23
Don't worry, that error seems to have occured with a dodgy change of PATH.

Will try again

---

### Post by andrew102 on 2014-04-23
No errors now. Can anyone tell me how to properly pipe the output of git to a log file so I can check it's working. Sometimes it works, other times it doesn't even when using --progress

---

### Post by papibe on 2014-04-23
I'm glad you are making some progress.

My guess is that some of the output is being redirected to the standard error. In order to redirected back to the standard output so that 'all' is redirected to a file use something like this:
```
git push --progress >> log_file.log 2>&1
```
Hope it helps. Let us know how that worked.
Regards.

---

### Post by andrew102 on 2014-04-27
That seems to give the normal terminal output - thanks!!

---


---
title: "Dynamically Propagating Configuration Changes"
date: 2012-12-02
forum: General Help
---

### Post by expelledboy on 2012-12-02
Hey!

I just cant seem to find the right words to research what I want to do, and it follows that I am not going to be able to make clear what I want to achieve here, so please bear with me.

I more frequently that I would like:
- move to new distros, to try them out.
- upgrade my os, else risk falling into the stone age.
- reinstall my current distro, cause sometimes its just easier.
- move hardware platforms, and feel that a clean install is just "nicer".

Every time this happens I find myself amending configuration files to suit my requirements. I am not confident enough to just copy and replace the equivalent file from my previous system, given that you could override sections critical to that distro, or worse put something in place which subtly affects some other aspect of your system, that becomes unstable, which prevents locating the cause by debugging various error outputs.

So I just edit the files manually. Again, and again.

What I want is to be able to make a researched decision, once, about a particular setting in a configuration file, and have that decision propagated back into my fresh system automatically.

I dont mind writing a application to achieve this, however I am positive their are existing tools that can do this, or that almost, which I can use to make the task of writing the application easier.

At first I tried diff and patch, as suggested by someone on irc. For minor changes it worked, but in practice it was more work than just manually editing each file.

Then I had a look into sed. It works, mostly... I am sure it pays off, eventually...

So, any ideas?

---

### Post by Cheesehead on 2012-12-02
Seems like an ideal use case for a set of custom patches, based on what you describe. Patches are also easily portable, undoable, and trackable.
What makes them too difficult/inconvenient? Do you have an example?

---

### Post by expelledboy on 2012-12-02
Its possible (very likely) I am unaware of features available in patch that make this task trivial.

I don't have examples. I could presumably get two or three of the same configuration files across distros and explain my concerns with using patch from there.

What you will find is that the files each have their own set of configurations. Some have extensive commentary. Some the setting you want to change is present, and in another its not. On afew distros the entire file doesnt even exist, and in others its used to do more than just set afew settings. Sometimes that same configuration file is named differently, or is in another directory altogether.

Given my previous experience with patch I found that its purpose was to update a file, rather than amend it. What I mean by this is that the patching implies a) some kind of common ancestor and b) a progression to equality. Perhaps I'm wrong.

What I want to do is set one setting, by editing or adding it, without modifying the rest of the file at all.

---

### Post by oldfred on 2012-12-02
I install Ubuntu every 6 months and often reinstall the beta or RC also. And I have two computers. After reconfiguring the same settings a few times, I said enough. 

I searched for or saw someone post a command line way to edit and did all the updates that I wanted by command line. Then I listed history with history command and copied into a bash file. I still am editing before or after every install but run my script to do 80% or more of what I want.

---

### Post by Cheesehead on 2012-12-02
Based on the additional information, I agree with oldfred. Script-based search-and-replace or append seems likely to be easier for that use case than patching.

Sed, awk, grep & cut, whatever you are most familiar with.

---

### Post by expelledboy on 2012-12-03
> **oldfred said:**
> I install Ubuntu every 6 months and often reinstall the beta or RC also. And I have two computers. After reconfiguring the same settings a few times, I said enough. 

I searched for or saw someone post a command line way to edit and did all the updates that I wanted by command line. Then I listed history with history command and copied into a bash file. I still am editing before or after every install but run my script to do 80% or more of what I want.

Do you mind sharing your script, just for reference? Perhaps I can generalize it.

---

### Post by oldfred on 2012-12-03
I have two scripts. Some comments so oldfred can remember what he thought he wanted to do and many lines commented out. Those were old way and not sure if new worked so did not delete older. And some are things I have seen but have not implemented yet.

linkdata2home.sh adds my data partitions to fstab and links all the folders into /home. Has hardcoded UUIDs so only works for my desktop install. I have to change UUIDs for laptop. But I plan on changing to labels so then it is one script for both systems.

newinstall.sh installs applications. A lot is redundant as I also have a dpkg export of all installed apps from old install that should install everything.

If you have questions just ask. Cannot guarantee I even know answer.

---

### Post by expelledboy on 2012-12-03
Thanks. Its not quite what I am looking for though.

I actually used to have a similar set of scripts I called "actions", which are just bash scripts that do various tasks, such as: installTodotxt.sh, setShell2Zsh.sh, addSoundcard2AsoundConfig.sh, etc.

Each action included the following code, which causes the script to fail if any one command returned a non-zero value:
```

#!/bin/bash
set -e
set -o pipefail

```

And optionally if the action could be applied across platforms:
```

case `uname -a` in
  *CYGWIN*)
    # specialized action
    ;;
  *ARCH*)
    # specialized action
    ;;
  *Darwin*)
    # specialized action
    ;;
esac

```

From these I compiled "action lists", another bash script, which essentially tried to execute each of scripts I had specified in a list.

For example I had one called getMusicWorking.sh, which had these in the list:
- addSoundcard2AsoundConfig.sh
- installDlnaServer.sh
- installMusicPlayers.sh
- setAmpAdjustments.sh
- linkPersonalFiles.sh

If something failed it would put me into a vim session with a split view of the script that failed, and its stderr output.

Within vim I had shortcuts to execute the highlighted lines. So I modified everything till it worked, and manually executed the rest of the script.

When I quit the editor the action list would continue from the next action in the list.


But as I said I actually just want a tool to amend configuration files intelligently. :popcorn:

---


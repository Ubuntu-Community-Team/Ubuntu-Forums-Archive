---
title: "Installing Elm-Lang on Ubuntu 17.10"
date: 2017-11-02
forum: General Help
---

### Post by Hasimir on 2017-11-02
In the past months I managed to install and run on my machine all the needed components to work with the Elm-Language.
A few months ago I made a clean install of Ubuntu-Gnome 17.04, and did not reinstall the Elm stuff.
Now I upgraded to Ubuntu 17.10.
And am trying to install the Elm stuff.
And am failing.

Following [THIS]("https://guide.elm-lang.org/install.html") guide I started by installing the latest Nodejs 8.9.0 and NPM 5.5.1
No problem.
Then I tried running the elm install command
```
[COLOR=#4D4D4D][FONT=&amp]$ sudo npm install -g elm[/FONT][/COLOR]
```
I got a bunch of NPM errors
> 
npm WARN deprecated node-uuid@1.4.8: Use uuid module instead
/usr/bin/elm -> /usr/lib/node_modules/elm/binwrappers/elm
/usr/bin/elm-make -> /usr/lib/node_modules/elm/binwrappers/elm-make
/usr/bin/elm-reactor -> /usr/lib/node_modules/elm/binwrappers/elm-reactor
/usr/bin/elm-package -> /usr/lib/node_modules/elm/binwrappers/elm-package
/usr/bin/elm-repl -> /usr/lib/node_modules/elm/binwrappers/elm-repl


> elm@0.18.0 install /usr/lib/node_modules/elm
> node install.js


Error extracting linux-x64.tar.gz - Error: EACCES: permission denied, mkdir '/usr/lib/node_modules/elm/Elm-Platform'
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! elm@0.18.0 install: `node install.js`
npm ERR! Exit status 1
npm ERR! 
npm ERR! Failed at the elm@0.18.0 install script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.


Online a found a solution on [THIS]("https://github.com/elm-lang/elm-platform/issues/215") GitHub conversation.
It basically referred to the NPM official website describing this fix: [https://docs.npmjs.com/getting-started/fixing-npm-permissions](https://docs.npmjs.com/getting-started/fixing-npm-permissions)
My case was the number 2, so I followed those instructions.
At the step where I am supposed to edit the .profile file I'm not sure what to do...
The file already existed and contained this code:
```

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.


# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022


# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi


# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi



```

So I simply added one more line and pasted the new command, like this:
```
# ~/.profile: executed by the command interpreter for login shells.# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.


# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022


# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi


# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

export PATH=~/.npm-global/bin:$PATH

```

After that I tried installing ELM again... and apparently it worked, with this output:
> npm WARN deprecated node-uuid@1.4.8: Use uuid module instead/home/hasimir/.npm-global/bin/elm-make -> /home/hasimir/.npm-global/lib/node_modules/elm/binwrappers/elm-make
/home/hasimir/.npm-global/bin/elm -> /home/hasimir/.npm-global/lib/node_modules/elm/binwrappers/elm
/home/hasimir/.npm-global/bin/elm-package -> /home/hasimir/.npm-global/lib/node_modules/elm/binwrappers/elm-package
/home/hasimir/.npm-global/bin/elm-reactor -> /home/hasimir/.npm-global/lib/node_modules/elm/binwrappers/elm-reactor
/home/hasimir/.npm-global/bin/elm-repl -> /home/hasimir/.npm-global/lib/node_modules/elm/binwrappers/elm-repl


> elm@0.18.0 install /home/hasimir/.npm-global/lib/node_modules/elm
> node install.js


Downloading Elm binaries from [https://dl.bintray.com/elmlang/elm-platform/0.18.0/linux-x64.tar.gz](https://dl.bintray.com/elmlang/elm-platform/0.18.0/linux-x64.tar.gz)
+ elm@0.18.0
added 92 packages in 7.027s


But... here is my problem... the Elm program doesn't seem to be working :(
If I try any Elm command, the terminal says command not found.
If I try to run commands such as "elm -v" I get no command found.
With "which elm" I get nothing at all.
Only with "whereis elm" do I get an output: /usr/bin/elm

What could my problem be?

---

### Post by Hasimir on 2017-11-03
It turns out that the problem was the **.profile** file not being correctly updated after I modified it.
The command from terminal should have done it, but it did not.
A simple reboot did away with the problem.
And a bit of help from the guys on the official Elm Slack made clear what was the culprit.

---


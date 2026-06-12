---
title: "Problems with environment variables and devkitpro"
date: 2007-01-27
forum: General Help
---

### Post by petedee on 2007-01-27
Hey guys, hope you can help me out here
 
I'm wanting to create some DS homebrew games and since I'm working with a freind we've both agreed to run devkitpro. I've only being using ubuntu for a few days after I found out that devkitpro won't work with my new vista installation (surprised? me? nooooo) and I've being using windows for a long time so please bear with me whilst I find out where everything is.

So I've downloaded the nds librarys and devkitARM files from devkitpro.org, I've dropped them into my /usr/local/devkitPro directory like the [website]("http://www.devkitpro.org/setup.shtml") says and I'm trying to compile a sample, the problem is that when I try to run make on the source I get 
```
Makefile:6: *** "Please set DEVKITARM in your environment. export DEVKITARM=<path to>devkitARM".  Stop.

```

I know how to install the environmental variables with windows but where do they go in Ubuntu? I've read that i should put them in ~./bash_profile which i have done so it looks a little like this:
```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

PATH=/usr/bin
PATH=/usr/local/DevkitPro/devkitARM/bin
```

I have no idea if thats right tho.

I know that I've installed make using the "build-essential" package but is that the right package to use or is there a special one that should come with building for the ARM system?

Please help guys, I really need to get a dev environment up and running soon

---

### Post by tUrtleAE86 on 2007-01-30
To set env vars temporarily:

```
export MYVARIABLE="value"
```

To set them permanently, open your ~/.bash_profile file in gedit:

```
gedit ~/.bash_profile
```

Add the same export lines into the file, save and close the file.

And no, you don't have to reboot. :)
Just logout and log back in. (Quickest way is to press CTRL ALT BKSP, which restarts X).

Oh, and don't edit your PATH environment variable by simply assigning one value to it, it will overwrite your existing path.

Instead, do this:

```
export PATH=$PATH:/add/this/path
```

To check that your environment variables are set correctly:

```
echo $ENV_VARIABLE
```

Or:

```
env | grep ENV_VARIABLE
```

---


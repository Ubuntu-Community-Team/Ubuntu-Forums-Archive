---
title: "Check if certain software is install"
date: 2016-09-12
forum: General Help
---

### Post by sed_faster on 2016-09-12
Hello everyone,

I have the script which install some programs, but I need create a statement for check if determined software are install.
How can I do this for example, check if git is install?

Thanks

---

### Post by ian-weisser on 2016-09-12
It depends upon the install method.

If installing using apt, then simply ask apt (14.04 and newer).
```
$ apt list firefox
firefox/xenial-updates,xenial-security,now 48.0+build2-0ubuntu0.16.04.1 amd64 **[installed]**
```

You can also test for existence of the binary...if you know where that binary is supposed to be located.
```
$ test -x /bin/date && echo 'exists' || echo 'not'exists
exists

$ test -x /bin/no_such_application && echo 'exists' || echo 'not'
not
```

---

### Post by sed_faster on 2016-09-12
Thanks ian-weisser

The solution for apt serves. I need this for my script, if the software has been install the script won't run again.
My next goal is create a statement "if" to do check/read output this commands. When I finish I will share solution in this post!

Thanks

---

### Post by sisco311 on 2016-09-12
In addition to the above mentioned methods you can use `command', `hash', `type' or `which':

```

if command -v git >/dev/null 2>&1
then
    printf '%s\n' "git command exists" >&2
else
    printf '%s\n' "git: command not found" >&2
fi

``` 

See: [http://stackoverflow.com/questions/592620/check-if-a-program-exists-from-a-bash-script](http://stackoverflow.com/questions/592620/check-if-a-program-exists-from-a-bash-script)

---

### Post by sisco311 on 2016-09-12
> **Edgar_Oliveira said:**
> Thanks ian-weisser

The solution for apt serves. I need this for my script, if the software has been install the script won't run again.
My next goal is create a statement "if" to do check/read output this commands. When I finish I will share solution in this post!

Thanks

So, if I understand you correctly, you want to check if the application is installed by the package manager.

On Ubuntu/Debian, in a bash script, I would try something like:
```

if [[ $(dpkg-query > /dev/null 2>&1 --show --showformat='${db:Status-Status}\n' **package-name**) == installed ]]
then
    echo >&2 installed
fi

```

---

### Post by ian-weisser on 2016-09-12
Not sure why it's worth bothering to check.
If already installed, any new instruction to install will simply be ignored.

Simply create a list of top-level packages, and let apt sort out what's already installed and what is needed. Apt will handle it.
That's all apt does. That's apt's entire purpose for existing.

After a fresh install, I simply do 'sudo apt install sleepy grumpy doc dopey bashful' ... and let apt figure out the rest. There. All my software customization is done.

---

### Post by DuckHook on 2016-09-12
> **ian-weisser said:**
> ...After a fresh install, I simply do 'sudo apt install sleepy grumpy doc dopey bashful' ...That must get you a seriously awesome system!

I've wanted Mickey, Donald, Pluto and Minnie for ages, but have never figured out how. Who thought it would be as simple as using apt?

Ya' learn somethin' new every day…

---


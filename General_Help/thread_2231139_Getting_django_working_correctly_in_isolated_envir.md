---
title: "Getting django working correctly in isolated environment"
date: 2014-06-23
forum: General Help
---

### Post by samwillc on 2014-06-23
Hi,

I am trying to follow numerous tutorials about how to get a django project up and running. I'm new to it and wanted to give it a shot. However, it's driving me to distraction with so many different guides all doing slightly different things. I have python installed at:

```

/home/sam/.pyenv/versions/2.7.6/bin/python
/home/sam/.pyenv/versions/3.4.0/bin/python

```

This is fine, as I use eclipse for learning python and just point to these places. I can successfully write python programs and run them in eclipse. All good so far. So a few months down the line I thought I'd try django as I use Drupal CMS and wanted to expand my horizons.

I ran in terminal:

```

pip install virtualenvwrapper

```

Then according to the next bitpart of the guide ( [http://www.jeffknupp.com/blog/2013/12/18/starting-a-django-16-project-the-right-way/](http://www.jeffknupp.com/blog/2013/12/18/starting-a-django-16-project-the-right-way/) ), I need to type this:

```

export WORKON_HOME=$HOME/.virtualenvs
export PROJECT_HOME=$HOME/directory-you-do-development-in
source /usr/local/bin/virtualenvwrapper.sh

```

which fails, as my virtualenvwrapper.sh:

```

find / -name virtualenvwrapper.sh

```

is located  here:

```

/home/sam/.pyenv/versions/2.7.6/bin/virtualenvwrapper.sh
/home/sam/.pyenv/shims/virtualenvwrapper.sh

```

not here:

```

/usr/local/bin/virtualenvwrapper.sh

```

I'm quite confused about what to do here. In fact, my 'usr/local/bin/' directory contains nothing. I installed python quite a while ago so not 100% why I did it the way I did (with pyenv). I presume it was so I can avoid messing with the system installed version.

I also tried this:

```

sam@sam-pc:~$ pip install --install-option="--user" virtualenvwrapper
Requirement already satisfied (use --upgrade to upgrade): virtualenvwrapper in ./.pyenv/versions/2.7.6/lib/python2.7/site-packages
Requirement already satisfied (use --upgrade to upgrade): virtualenv in ./.pyenv/versions/2.7.6/lib/python2.7/site-packages (from virtualenvwrapper)
Requirement already satisfied (use --upgrade to upgrade): virtualenv-clone in ./.pyenv/versions/2.7.6/lib/python2.7/site-packages (from virtualenvwrapper)
Requirement already satisfied (use --upgrade to upgrade): stevedore in ./.pyenv/versions/2.7.6/lib/python2.7/site-packages (from virtualenvwrapper)
Cleaning up...
sam@sam-pc:~$ 

```

I thought this might put it in the 'usr/local/bin' location.

Anyway, any advice would be greatly appreciated so I can at least try django in an isolated environment (isolated being the key word because I'll probably screw something up)! Thanks.

---

### Post by samwillc on 2014-06-23
Ok, so I think I've got it working, just used in .bashrc:

```

export WORKON_HOME=$HOME/.virtualenvs
export PROJECT_HOME=$HOME/Python/projects
source ~/.pyenv/shims/virtualenvwrapper.sh

```

Then:

```

mkvirtualenv myDjangoProject

```

Now I have this directory:

```

/home/sam/.virtualenvs/myDjangoProject

```

then:

```

pip install Django

```

and Django appears to be installed at:

```

/home/sam/.virtualenvs/myDjangoProject/lib/python2.7/site-packages/django

```

Not sure if this is 'correct' or not but it's good enough for now.

---


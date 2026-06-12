---
title: "Software versions in Ubuntu repositories are well behind current versions"
date: 2013-06-21
forum: General Help
---

### Post by lmullen on 2013-06-21
I'm a relative newcomer to Ubuntu, though not to *nix systems and tools in general. I've noticed that for almost all of the programs that I use every day, the versions in the Ubuntu repositories are well behind the current versions. For example,

[LIST]
[*]Pandoc's current release: pandoc 1.11.1 (2013-03-17)
[*]Pandoc in Ubuntu repository: pandoc 1.10.1
[*]R current version: R version 3.0.1 (Good Sport) has been released on 2013-05-16.
[*]R in Ubuntu repository: R version 2.15.2 (2012-10-26)
[*]No option for Ruby 2.0.*
[/LIST]

What is the best thing to do if I want to use up-to-date versions? Should I learn how to update Ubuntu packages myself? (Not really interested in that for now.) Should I compile all of these programs from source? Or are there other repositories that I should add to apt-get and synaptic?

---

### Post by TheFu on 2013-06-21
Ubuntu is more about stability and interoperability than running on the bleeding edge. Other distros handle bleeding edge better by making those tools available and breaking from time to time.  Check out Arch or Gentoo.

However, Debian/Ubuntu does allow individuals to create PPAs which can be used by software developers to make their bleeding edge versions available and maintainable by average people running Ubuntu or Debian-based distros.  I would seek out a reputable PPA provider for each of the tools you want to run. Of course, a non-reputable PPA can be an easy way to get viruses and pwnd under Linux.

I don't know anyhting about Pandoc or R, so I can't recommend a solution, but I do know a little about Ruby.  Ruby developers (and this applies to anyone doing programming with Perl, Python, Php, java, and other fast changing languages) need to use a different language management method. We need to avoid using the platform/distro versions for our projects.  For Ruby, **rvm** or something similar is a best-practice.  For Perl, perlbrew - there is something similar for Python, I'm certain.

Stability is critical for the OS.  It is impossible for a distro to stay current AND stay stable with fast changing languages.  For ruby dependencies, look for a gist on the items to be pre-installed on github.  found it - [https://gist.github.com/cajun-code](https://gist.github.com/cajun-code) and look for rvm.

---

### Post by Impavidus on 2013-06-21
Each Ubuntu version stays with the same software versions throughout its life, except for some bug fixes, security patches and a few programs like firefox. If you're using 12.04 LTS these versions are over a year old (and occasionally even older). Using the intermediate Ubuntu versions (13.04 at the moment) gives you more recent software and often you can use PPAs. Or use a different Linux distro.

---

### Post by lmullen on 2013-06-21
Thanks for the advice. I suspected that there was something like PPAs, but I didn't know what to search for.

For R (a statistical programming language) there a reputable PPA from the CRAN repository. I found the [instructions for adding it here]("http://www.personal.psu.edu/mar36/blogs/the_ubuntu_r_blog/installing-r.html").

I've been building my own Rubies on OS X using rbenv and ruby-build. I was surprised that the version of ruby-build in Ubuntu doesn't have 2.0.*. Perhaps I need to find a PPA for Ruby too.

---

### Post by TheFu on 2013-06-21
> **lmullen said:**
> Thanks for the advice. I suspected that there was something like PPAs, but I didn't know what to search for.

For R (a statistical programming language) there a reputable PPA from the CRAN repository. I found the [instructions for adding it here]("http://www.personal.psu.edu/mar36/blogs/the_ubuntu_r_blog/installing-r.html").

I've been building my own Rubies on OS X using rbenv and ruby-build. I was surprised that the version of ruby-build in Ubuntu doesn't have 2.0.*. Perhaps I need to find a PPA for Ruby too.

For Ruby coders, using a PPA really isn't an option, since it doesn't also manage compatible gems. You should use either rbenv or rmv to manage your rubies, gems and ruby environments. This is a best practice and **woe to those** who don't follow it.  I can't overstate how important this is.

If you are a once-a-month ruby hacker, go ahead and find a PPA, but be aware that mixing system rubies and different PPA rubies is dangerous. Some system programs and scripts might (probably) will not work if you do this. That will be bad.  If you plan to use puppet (puppet is a ruby-based system config management tool) from the repositories, then you absolutely **must** stick with the ruby version from the same repo to avoid issues.  Most developers won't need puppet, but there are other ruby-based tools in the repositories.  Basically, I'm trying to say "**don't cross the streams.**"

---

### Post by lmullen on 2013-06-23
I installed rbenv and ruby-build directly from GitHub and build my own Rubies. That's what I was doing on OS X, but I thought there might be a better way on Ubuntu.

Pandoc I compiled with Cabal. Not so bad if it's the only Haskell platform you have to compile.

---

### Post by TheFu on 2013-06-23
> **lmullen said:**
> I installed rbenv and ruby-build directly from GitHub and build my own Rubies. That's what I was doing on OS X, but I thought there might be a better way on Ubuntu.

Using software in the repositories or a reputable PPA is definitely a best practice and I'd never suggest anyone except programmers use source packages if they can do it any other way.  Long term system patching and maintenance is one of the reasons that APT is so much better than all other solutions in the world ... including Apple, Microsoft, Oracle, Redhat, Adobe, .... 

However, someone writing ruby code for anything non-trivial or for their job **needs** to use an environment manager. How else do you have multiple ruby and rails versions on a system and not trip over the incompatibilities all the time?

Anyway, glad we could help in some way. Thanks for marking this SOLVED.

---


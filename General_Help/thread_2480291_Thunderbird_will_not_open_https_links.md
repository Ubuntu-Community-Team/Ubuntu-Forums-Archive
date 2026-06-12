---
title: "Thunderbird will not open https links"
date: 2022-10-24
forum: General Help
---

### Post by rcdawson on 2022-10-24
Kubuntu version 2022.04-1.  When I click on an https link in Thunderbird nothing happens, or at least nothing that I can observe.  It doesn't open a browser or ask what to do.  I followed the troubleshooting instructions on Mozilla's site, and found nothing wrong.  I have this problem on two computers, one with a clean install and one that was upgraded from Kubuntu 2020.04.  In both cases I moved my Thunderbird profile to the new computer.  I have two other computers on which it works fine and which I also moved by profile in the same way.  Is anyone else having this problem?  Does anyone have a solution.  I can share more information about the results of my troubleshooting if anyone is interested.

---

### Post by TheFu on 2022-10-24
Thunderbird is an email program. It shouldn't open any HTTP/s website.

Now, if you want Thunderbird to use the xdg-open command to pass the URL to the default browser, then both Thunderbird and your browser need to be setup to "connect".  I don't have 22.04, but suspect that thunderbird and firefox are both installed as snap packages.  These each run a little sandbox for security reasons. Snap packages can have connectors to allow specific programs to communicate.

You can get a list of available connectors:
```
$ snap     connections    thunderbird   --all   
```

[https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces) is the overview explanation.

It may be easier to remove all snaps and install non-snap versions of thunderbird and your preferred browser. IDK.  Snaps have many good things and many bad things about them.  This is one of the bad things.

Of course, if the thunderbird package on your system isn't a snap, then none of that will help.  OTOH, firefox and chromium browsers are both snap packages on 22.04, which would be the other half of the issue.

---

### Post by donald187 on 2022-10-25
On my computer running Ubuntu 22.04 Thunderbird came preinstalled as a .deb.  I've uninstalled it and installed Thunderbird as a snap.

```

$ apt policy thunderbird
thunderbird:
  Installed: (none)
  Candidate: 1:102.2.2+build1-0ubuntu0.22.04.1
  Version table:
     1:102.2.2+build1-0ubuntu0.22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:91.8.0+build2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

The snap Thunderbird opens https links in Firefox just fine with no action needed on my part to make this possible.

Hope this helps the OP.

EDIT:  Firefox is also a snap on my system.

---

### Post by rcdawson on 2022-10-26
Thank you for clarifying the process whereby my clicking on a link in my email causes firefox (or other browser) to open the link.  

My 2022.04-1 installation had firefox as a snap, but thunderbird as an installed package.  I did find a few other complaints about the problem, but no real resolution.  One person reported having solved the problem by reinstalling from the 2022.04-0. I did that, and the problem disappeared.  I then proceeded to upgrade without the problem recurring.  

Not a very satisfying solution, but I'm happy to have the functionality back.

---


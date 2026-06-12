---
title: "Maintain installed deb packages in APT Cache Archives"
date: 2017-01-19
forum: General Help
---

### Post by darkaten1 on 2017-01-19
Is there a mechanism in apt-get to pull all the deb packages for all the applications that I have installed from the repos including their dependencies and store them in the archives without reinstalling all my applications?

I recently retrained my brain to use apt instead of apt-get for installing and updating my desktop (Ubuntu 16.04 Desktop). The other day I found out that apt does not keep installed deb packages in /var/cache/apt/archives like apt-get. Apparently it clears the deb packages once the application is installed. I checked my archives and sure enough the applications that I have installed with apt are not in my archives. Normally I would say this is a good thing. However, I need those deb packages in the archives. We have a tool that pulls those deb packages so that we can easily update systems that we are running in very remote locations that have limited or no internet access.

---


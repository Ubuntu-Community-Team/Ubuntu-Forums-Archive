---
title: "Add Missing Maven Dependencies"
date: 2020-04-18
forum: General Help
---

### Post by ptmuldoon on 2020-04-18
I'm trying install on Ubuntu Server 19 the game PrendYourXyzzy, a cards against humanity clone, and I followed these older instructions found here:

[https://gist.github.com/beminee/e1670f449d82c96bac55107c9c37da00](https://gist.github.com/beminee/e1670f449d82c96bac55107c9c37da00)

I was able to get to the point in trying to make the build, but then the Maven build fails stating it is missing dependencies, and I am struggling to find how to add them.  I am unfamiliar with how Maven works and how to proceed.

This is the error I receive.

> 
[WARNING] The POM for com.fasterxml.jackson.core:jackson-databind:jar:2.10.1-SNAPSHOT is missing, no dependency information available
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.853 s
[INFO] Finished at: 2020-04-19T00:25:19Z
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal on project pyx: Could not resolve dependencies for project net.socialgamer:pyx:jar:0.7.0-SNAPSHOT: Failed to collect dependencies at com.maxmind.geoip2:geoip2:jar:2.8.0 -> com.maxmind.db:maxmind-db:jar:1.2.1 -> com.fasterxml.jackson.core:jackson-databind:jar:2.9.0,pr4-SNAPSHOT: Failed to read artifact descriptor for com.fasterxml.jackson.core:jackson-databind:jar:2.9.0,pr4-SNAPSHOT: Failure to find com.fasterxml.jackson:jackson-bom:pom:2.9.0.pr4-SNAPSHOT in [https://hibernate-sqlite.googlecode.com/svn/trunk/mavenrepo](https://hibernate-sqlite.googlecode.com/svn/trunk/mavenrepo) was cached in the local repository, resolution will not be reattempted until the update interval of hibernatesqlite-maven has elapsed or updates are forced -> [Help 1]
[ERROR] 
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR] 
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] [http://cwiki.apache.org/confluence/display/MAVEN/DependencyResolutionException](http://cwiki.apache.org/confluence/display/MAVEN/DependencyResolutionException)


---


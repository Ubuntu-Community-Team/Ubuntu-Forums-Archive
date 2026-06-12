---
title: "cocoon 2.1.10 installation trouble on feisty please help"
date: 2007-07-17
forum: General Help
---

### Post by zeroreference on 2007-07-17
Hi, this is my first post, so i apologize for any lacking info, etc.

I have been trying to install cocoon 2.1.10 on feisty fawn (7.04) and running into an
error on the build that i haven't been able to find anything about online (forums, google, etc).

I have java 1.6.0 and it seems to fine as the "java-version" command spits out the right stuff.


my JAVA_HOME is "/usr/lib/jvm/java-6-sun"

my PATH is "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-6-sun/bin:"

(both of these were confirmed from the command line as i am writing this).


I have tomcat 5.something up and running.


when i run **sudo ./build.sh**, (which should be the normal build, i'm not modifying the blocks or anything),  along with normal-seeming output, i get a lot of warnings that look like this:



...[B]/cocoon-2.1.10/src/java/org/apache/cocoon/reading/ImageReader.java:40: warning: com.sun.image.codec.jpeg.JPEGCodec is Sun proprietary API and may be removed in a future release
import com.sun.image.codec.jpeg.JPEGCodec;[/B]



however i think what is causing the build to fail is this:



[B]/home/myname/cocoon-2.1.10/src/blocks/databases/java/org/apache/cocoon/databases/ibatis/ExcaliburDataSourceFactory.java:82: org.apache.cocoon.databases.ibatis.ExcaliburDataSourceFactory.DataSourceWrapper is not abstract and does not override abstract method isWrapperFor(java.lang.Class<?>) in java.sql.Wrapper
    protected static final class DataSourceWrapper implements DataSource {
                           ^
[/B]

and this is the last bit of output:

[B]
Note: Some input files use unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.
1 error

BUILD FAILED
/home/myname/cocoon-2.1.10/tools/targets/compile-build.xml:263: The following error occurred while executing this line:
/home/myname/cocoon-2.1.10/build/cocoon/temp/blocks-build.xml:1633: The following error occurred while executing this line:
/home/myname/cocoon-2.1.10/build/cocoon/temp/blocks-build.xml:95: Compile failed; see the compiler error output for details.[/B]


please help, and let me know what more information i can provide. I am pretty clueless and frustrated at this point.

Thank you.

zr

---

### Post by wayneredmon on 2007-08-29
I've not tried a JVM 1.6 build, but I'm able to build a complete cocoon 2.1.10 war under java version 1.5.0_11.

Imported the war file into Eclipse 3.2 and it runs under Tomcat server 5.5 (under Eclipse).

Cocoon 2.1.10 WAR built on Feisty, AMD64-bit, using 1.5.0_11 JVM, Eclipse 3.2, Tomcat 5.5.x, cocoon 2.1.10.

---


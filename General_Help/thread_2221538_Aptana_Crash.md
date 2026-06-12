---
title: "Aptana Crash"
date: 2014-05-02
forum: General Help
---

### Post by falven on 2014-05-02
Hi,
I realize that this may be an Aptana issue, and I should post in their support (StackOverflow).
 However I have posted on StackOverflow and nobody has come to my aid :/
I was hoping someone here may be able to help. Especially since this issue is probably with my Ubuntu configuration and not Aptana itself.

Have latest Sun JDK - /usr/lib/jvm/java-8-oracle Changed /usr/bin/javaxxxx symlinks to reference JDK.


  [IMG]http://i.stack.imgur.com/oaJQ5.png[/IMG]


  Aptana Opens normally, however, Window -> Show View -> WebBrowser


  [IMG]http://i.stack.imgur.com/ziRlj.png[/IMG]
  
And

  Window -> Show View -> Web Browser Editor -> Crashes Aptana.

  
Verification that swig is installed:


  [IMG]http://i.stack.imgur.com/vSOrr.png[/IMG]

---

### Post by dragonfly41 on 2014-05-02
Although I haven't used Aptana recently I have Aptana Studio 3 (stand alone *sans* eclipse) running in Ubuntu 12.04 32 bit.

Aptana Studio 3, build: 3.4.2.201308081805

```
~$ java -version
java version "1.7.0_51"
Java(TM) SE Runtime Environment (build 1.7.0_51-b13)
Java HotSpot(TM) Server VM (build 24.51-b03, mixed mode)
```


I'm not sure if this is your first time usage of Aptana (eclipse mode). Has this error just occurred?

I see that you have also posted on stackoverflow ..

[http://stackoverflow.com/questions/23420428/could-not-create-the-view-swigdirector-cefhandler-handlebeforecreated](http://stackoverflow.com/questions/23420428/could-not-create-the-view-swigdirector-cefhandler-handlebeforecreated)

...

Comparing with my setup ...

First selecting web perspective .. 
I can apply Window -> Show View -> Web Browser

```
swig -version
The program 'swig' is currently not installed.  You can install it by typing:
sudo apt-get install swig
```

which is to be expected since I don't have Eclipse installed.

...

Some thoughts ..

If you start a fresh workspace do you see this same stack?

Can you run stand alone Aptana Studio?

...

searching ... "could not create the view: SwigDirector_CefHandler_HandleBeforeCreated"

I've read from some threads that deleting jdt settings from workspace ./metadata/plugins has worked for others with this error.

---

### Post by falven on 2014-05-02
Hey dragon,
Thanks for the input.
I am running the Standalone version of Aptana Studio 3 (It uses Eclipse) as well. Not the plugin.
Yes, I posted on StackOverflow as I mentioned.

Just tried with a fresh workspace. Same exact error/problems. :/
When I deleted the plugins directory you specified, aptana crashed on the next launch, and on the following, it still displays the exact error/problems when opening the webbrowser view.
I'm so stumped.

---

### Post by dragonfly41 on 2014-05-02
You could try ..

Aptana > Help > Aptana > Run Diagnostic Test

and compare with my output as follows .. it might show up something ..

```

Host OS: Linux
OS Version: 3.2.0-60-generic-pae
OS Arch: x86

JRE Version: 1.7.0_51
JRE Vendor: Oracle Corporation
JRE Home: /usr/lib/jvm/java-7-oracle/jre

Aptana Studio 3 Version: 3.4.2.201308081805
Install Directory: file:/opt/Aptana_Studio_3.4.2/
Workspace Directory: file:/home/dl/Documents/Aptana Studio 3 Workspace/
VM Arguments: -Xms40m
-Xmx512m
-Declipse.p2.unsignedPolicy=allow
-Declipse.log.size.max=10000
-Declipse.log.backup.max=5
-Djava.awt.headless=true
-XX:MaxPermSize=256m
-Djava.class.path=/opt/Aptana_Studio_3.4.2//plugins/org.eclipse.equinox.launcher_1.2.0.v20110502.jar

Language: en_GB

Node.JS Version: v0.10.26
NPM Path: /usr/bin/npm
NPM Version: 1.4.3
/usr/lib
&#9500;&#9472;&#9516; browserify@3.20.0
&#9474; &#9500;&#9472;&#9472; assert@1.1.0
&#9474; &#9500;&#9472;&#9516; browser-pack@2.0.1
&#9474; &#9474; &#9500;&#9472;&#9516; combine-source-map@0.3.0
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; convert-source-map@0.3.3
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; inline-source-map@0.3.0
&#9474; &#9474; &#9474; &#9492;&#9472;&#9516; source-map@0.1.31
&#9474; &#9474; &#9474;   &#9492;&#9472;&#9472; amdefine@0.1.0
&#9474; &#9474; &#9492;&#9472;&#9516; JSONStream@0.6.4
&#9474; &#9474;   &#9500;&#9472;&#9472; jsonparse@0.0.5
&#9474; &#9474;   &#9492;&#9472;&#9472; through@2.2.7
&#9474; &#9500;&#9472;&#9516; browser-resolve@1.2.2
&#9474; &#9474; &#9492;&#9472;&#9472; resolve@0.6.1
&#9474; &#9500;&#9472;&#9516; concat-stream@1.4.1
&#9474; &#9474; &#9500;&#9472;&#9516; readable-stream@1.1.10
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; core-util-is@1.0.1
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; debuglog@0.0.2
&#9474; &#9474; &#9492;&#9472;&#9472; typedarray@0.0.5
&#9474; &#9500;&#9472;&#9472; console-browserify@1.0.3
&#9474; &#9500;&#9472;&#9472; constants-browserify@0.0.1
&#9474; &#9500;&#9472;&#9472; crypto-browserify@1.0.9
&#9474; &#9500;&#9472;&#9472; deep-equal@0.1.2
&#9474; &#9500;&#9472;&#9472; defined@0.0.0
&#9474; &#9500;&#9472;&#9516; deps-sort@0.1.1
&#9474; &#9474; &#9492;&#9472;&#9516; JSONStream@0.6.4
&#9474; &#9474;   &#9500;&#9472;&#9472; jsonparse@0.0.5
&#9474; &#9474;   &#9492;&#9472;&#9472; through@2.2.7
&#9474; &#9500;&#9472;&#9472; domain-browser@1.1.1
&#9474; &#9500;&#9472;&#9472; duplexer@0.1.1
&#9474; &#9500;&#9472;&#9472; events@1.0.0
&#9474; &#9500;&#9472;&#9516; http-browserify@1.1.0
&#9474; &#9474; &#9492;&#9472;&#9472; Base64@0.2.0
&#9474; &#9500;&#9472;&#9472; https-browserify@0.0.0
&#9474; &#9500;&#9472;&#9472; inherits@2.0.1
&#9474; &#9500;&#9472;&#9516; insert-module-globals@2.3.0
&#9474; &#9474; &#9500;&#9472;&#9472; commondir@0.0.1
&#9474; &#9474; &#9500;&#9472;&#9516; lexical-scope@0.0.15
&#9474; &#9474; &#9474; &#9492;&#9472;&#9516; astw@0.0.0
&#9474; &#9474; &#9474;   &#9492;&#9472;&#9472; esprima@1.0.2
&#9474; &#9474; &#9492;&#9472;&#9472; process@0.5.2
&#9474; &#9500;&#9472;&#9516; JSONStream@0.7.1
&#9474; &#9474; &#9500;&#9472;&#9472; jsonparse@0.0.5
&#9474; &#9474; &#9492;&#9472;&#9472; through@2.2.7
&#9474; &#9500;&#9472;&#9472; minimist@0.0.5
&#9474; &#9500;&#9472;&#9516; module-deps@1.2.2
&#9474; &#9474; &#9500;&#9472;&#9516; detective@2.1.2
&#9474; &#9474; &#9474; &#9500;&#9472;&#9516; escodegen@0.0.15
&#9474; &#9474; &#9474; &#9474; &#9492;&#9472;&#9516; source-map@0.1.31
&#9474; &#9474; &#9474; &#9474;   &#9492;&#9472;&#9472; amdefine@0.1.0
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; esprima@1.0.2
&#9474; &#9474; &#9492;&#9472;&#9472; resolve@0.6.1
&#9474; &#9500;&#9472;&#9516; native-buffer-browserify@2.0.8
&#9474; &#9474; &#9500;&#9472;&#9472; base64-js@0.0.6
&#9474; &#9474; &#9492;&#9472;&#9472; ieee754@1.1.1
&#9474; &#9500;&#9472;&#9472; os-browserify@0.1.1
&#9474; &#9500;&#9472;&#9472; parents@0.0.2
&#9474; &#9500;&#9472;&#9472; path-browserify@0.0.0
&#9474; &#9500;&#9472;&#9472; punycode@1.2.3
&#9474; &#9500;&#9472;&#9472; querystring@0.2.0
&#9474; &#9500;&#9472;&#9472; shell-quote@0.0.1
&#9474; &#9500;&#9472;&#9516; stream-browserify@0.1.2
&#9474; &#9474; &#9492;&#9472;&#9472; process@0.5.2
&#9474; &#9500;&#9472;&#9472; stream-combiner@0.0.4
&#9474; &#9500;&#9472;&#9472; string_decoder@0.0.1
&#9474; &#9500;&#9472;&#9516; syntax-error@0.0.1
&#9474; &#9474; &#9492;&#9472;&#9472; esprima@0.9.9
&#9474; &#9500;&#9472;&#9472; through@2.3.4
&#9474; &#9500;&#9472;&#9516; timers-browserify@1.0.1
&#9474; &#9474; &#9492;&#9472;&#9472; process@0.5.2
&#9474; &#9500;&#9472;&#9472; tty-browserify@0.0.0
&#9474; &#9500;&#9472;&#9516; umd@2.0.0
&#9474; &#9474; &#9500;&#9472;&#9516; rfile@1.0.0
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; callsite@1.0.0
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; resolve@0.3.1
&#9474; &#9474; &#9500;&#9472;&#9516; ruglify@1.0.0
&#9474; &#9474; &#9474; &#9492;&#9472;&#9516; uglify-js@2.2.5
&#9474; &#9474; &#9474;   &#9500;&#9472;&#9516; optimist@0.3.7
&#9474; &#9474; &#9474;   &#9474; &#9492;&#9472;&#9472; wordwrap@0.0.2
&#9474; &#9474; &#9474;   &#9492;&#9472;&#9516; source-map@0.1.31
&#9474; &#9474; &#9474;     &#9492;&#9472;&#9472; amdefine@0.1.0
&#9474; &#9474; &#9492;&#9472;&#9516; uglify-js@2.4.9
&#9474; &#9474;   &#9500;&#9472;&#9472; async@0.2.9
&#9474; &#9474;   &#9500;&#9472;&#9516; optimist@0.3.7
&#9474; &#9474;   &#9474; &#9492;&#9472;&#9472; wordwrap@0.0.2
&#9474; &#9474;   &#9500;&#9472;&#9516; source-map@0.1.31
&#9474; &#9474;   &#9474; &#9492;&#9472;&#9472; amdefine@0.1.0
&#9474; &#9474;   &#9492;&#9472;&#9472; uglify-to-browserify@1.0.1
&#9474; &#9500;&#9472;&#9516; url@0.7.9
&#9474; &#9474; &#9500;&#9472;&#9472; punycode@1.0.0
&#9474; &#9474; &#9492;&#9472;&#9472; querystring@0.1.0
&#9474; &#9500;&#9472;&#9472; util@0.10.2
&#9474; &#9500;&#9472;&#9516; vm-browserify@0.0.2
&#9474; &#9474; &#9492;&#9472;&#9472; indexof@0.0.1
&#9474; &#9492;&#9472;&#9516; zlib-browserify@0.0.3
&#9474;   &#9492;&#9472;&#9516; tape@0.2.2
&#9474;     &#9500;&#9472;&#9472; deep-equal@0.0.0
&#9474;     &#9492;&#9472;&#9472; jsonify@0.0.0
&#9500;&#9472;&#9472; coffee-script@1.6.3
&#9500;&#9472;&#9516; grunt-cli@0.1.11
&#9474; &#9500;&#9472;&#9516; findup-sync@0.1.2
&#9474; &#9474; &#9500;&#9472;&#9516; glob@3.1.21
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; graceful-fs@1.2.3
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; inherits@1.0.0
&#9474; &#9474; &#9474; &#9492;&#9472;&#9516; minimatch@0.2.12
&#9474; &#9474; &#9474;   &#9500;&#9472;&#9472; lru-cache@2.5.0
&#9474; &#9474; &#9474;   &#9492;&#9472;&#9472; sigmund@1.0.0
&#9474; &#9474; &#9492;&#9472;&#9472; lodash@1.0.1
&#9474; &#9500;&#9472;&#9516; nopt@1.0.10
&#9474; &#9474; &#9492;&#9472;&#9472; abbrev@1.0.4
&#9474; &#9492;&#9472;&#9472; resolve@0.3.1
&#9500;&#9472;&#9516; less@1.5.0
&#9474; &#9500;&#9472;&#9516; clean-css@1.0.12
&#9474; &#9474; &#9492;&#9472;&#9516; commander@1.3.2
&#9474; &#9474;   &#9492;&#9472;&#9472; keypress@0.1.0
&#9474; &#9500;&#9472;&#9472; mime@1.2.11
&#9474; &#9500;&#9472;&#9472; mkdirp@0.3.5
&#9474; &#9500;&#9472;&#9516; request@2.27.0
&#9474; &#9474; &#9500;&#9472;&#9472; aws-sign@0.3.0
&#9474; &#9474; &#9500;&#9472;&#9472; cookie-jar@0.3.0
&#9474; &#9474; &#9500;&#9472;&#9472; forever-agent@0.5.0
&#9474; &#9474; &#9500;&#9472;&#9516; form-data@0.1.2
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; async@0.2.9
&#9474; &#9474; &#9474; &#9492;&#9472;&#9516; combined-stream@0.0.4
&#9474; &#9474; &#9474;   &#9492;&#9472;&#9472; delayed-stream@0.0.5
&#9474; &#9474; &#9500;&#9472;&#9516; hawk@1.0.0
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; boom@0.4.2
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; cryptiles@0.2.2
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; hoek@0.9.1
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; sntp@0.2.4
&#9474; &#9474; &#9500;&#9472;&#9516; http-signature@0.10.0
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; asn1@0.1.11
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; assert-plus@0.1.2
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; ctype@0.5.2
&#9474; &#9474; &#9500;&#9472;&#9472; json-stringify-safe@5.0.0
&#9474; &#9474; &#9500;&#9472;&#9472; node-uuid@1.4.1
&#9474; &#9474; &#9500;&#9472;&#9472; oauth-sign@0.3.0
&#9474; &#9474; &#9500;&#9472;&#9472; qs@0.6.5
&#9474; &#9474; &#9492;&#9472;&#9472; tunnel-agent@0.3.0
&#9474; &#9492;&#9472;&#9516; source-map@0.1.30
&#9474;   &#9492;&#9472;&#9472; amdefine@0.1.0
&#9500;&#9472;&#9516; npm@1.4.3
&#9474; &#9500;&#9472;&#9472; abbrev@1.0.4
&#9474; &#9500;&#9472;&#9472; ansi@0.2.1
&#9474; &#9500;&#9472;&#9472; ansicolors@0.3.2
&#9474; &#9500;&#9472;&#9472; ansistyles@0.1.3
&#9474; &#9500;&#9472;&#9472; archy@0.0.2
&#9474; &#9500;&#9472;&#9472; block-stream@0.0.7
&#9474; &#9500;&#9472;&#9472; child-process-close@0.1.1
&#9474; &#9500;&#9472;&#9472; chmodr@0.1.0
&#9474; &#9500;&#9472;&#9472; chownr@0.0.1
&#9474; &#9500;&#9472;&#9472; cmd-shim@1.1.1
&#9474; &#9500;&#9472;&#9472; columnify@0.1.2
&#9474; &#9500;&#9472;&#9472; editor@0.0.5
&#9474; &#9500;&#9472;&#9472; fstream@0.1.25
&#9474; &#9500;&#9472;&#9516; fstream-npm@0.1.6
&#9474; &#9474; &#9492;&#9472;&#9472; fstream-ignore@0.0.7
&#9474; &#9500;&#9472;&#9472; github-url-from-git@1.1.1
&#9474; &#9500;&#9472;&#9472; github-url-from-username-repo@0.0.2
&#9474; &#9500;&#9472;&#9472; glob@3.2.7
&#9474; &#9500;&#9472;&#9472; graceful-fs@2.0.2
&#9474; &#9500;&#9472;&#9472; inherits@2.0.1
&#9474; &#9500;&#9472;&#9472; ini@1.1.0
&#9474; &#9500;&#9472;&#9516; init-package-json@0.0.14
&#9474; &#9474; &#9492;&#9472;&#9472; promzard@0.2.1
&#9474; &#9500;&#9472;&#9472; lockfile@0.4.2
&#9474; &#9500;&#9472;&#9472; lru-cache@2.5.0
&#9474; &#9500;&#9472;&#9516; minimatch@0.2.14
&#9474; &#9474; &#9492;&#9472;&#9472; sigmund@1.0.0
&#9474; &#9500;&#9472;&#9472; mkdirp@0.3.5
&#9474; &#9500;&#9472;&#9472; node-gyp@0.12.2
&#9474; &#9500;&#9472;&#9472; nopt@2.2.0
&#9474; &#9500;&#9472;&#9472; npm-install-checks@1.0.0
&#9474; &#9500;&#9472;&#9472; npm-registry-client@0.4.4
&#9474; &#9500;&#9472;&#9472; npm-user-validate@0.0.3
&#9474; &#9500;&#9472;&#9516; npmconf@0.1.12
&#9474; &#9474; &#9492;&#9472;&#9516; config-chain@1.1.8
&#9474; &#9474;   &#9492;&#9472;&#9472; proto-list@1.2.2
&#9474; &#9500;&#9472;&#9472; npmlog@0.0.6
&#9474; &#9500;&#9472;&#9472; once@1.3.0
&#9474; &#9500;&#9472;&#9472; opener@1.3.0
&#9474; &#9500;&#9472;&#9472; osenv@0.0.3
&#9474; &#9500;&#9472;&#9472; path-is-inside@1.0.0
&#9474; &#9500;&#9472;&#9516; read@1.0.5
&#9474; &#9474; &#9492;&#9472;&#9472; mute-stream@0.0.4
&#9474; &#9500;&#9472;&#9472; read-installed@1.0.0
&#9474; &#9500;&#9472;&#9516; read-package-json@1.1.7
&#9474; &#9474; &#9492;&#9472;&#9472; normalize-package-data@0.2.9
&#9474; &#9500;&#9472;&#9516; request@2.30.0
&#9474; &#9474; &#9500;&#9472;&#9472; aws-sign2@0.5.0
&#9474; &#9474; &#9500;&#9472;&#9472; forever-agent@0.5.0
&#9474; &#9474; &#9500;&#9472;&#9516; form-data@0.1.2
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; async@0.2.9
&#9474; &#9474; &#9474; &#9492;&#9472;&#9516; combined-stream@0.0.4
&#9474; &#9474; &#9474;   &#9492;&#9472;&#9472; delayed-stream@0.0.5
&#9474; &#9474; &#9500;&#9472;&#9516; hawk@1.0.0
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; boom@0.4.2
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; cryptiles@0.2.2
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; hoek@0.9.1
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; sntp@0.2.4
&#9474; &#9474; &#9500;&#9472;&#9516; http-signature@0.10.0
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; asn1@0.1.11
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; assert-plus@0.1.2
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; ctype@0.5.2
&#9474; &#9474; &#9500;&#9472;&#9472; json-stringify-safe@5.0.0
&#9474; &#9474; &#9500;&#9472;&#9472; mime@1.2.11
&#9474; &#9474; &#9500;&#9472;&#9472; node-uuid@1.4.1
&#9474; &#9474; &#9500;&#9472;&#9472; oauth-sign@0.3.0
&#9474; &#9474; &#9500;&#9472;&#9472; qs@0.6.6
&#9474; &#9474; &#9500;&#9472;&#9516; tough-cookie@0.9.15
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; punycode@1.2.3
&#9474; &#9474; &#9492;&#9472;&#9472; tunnel-agent@0.3.0
&#9474; &#9500;&#9472;&#9472; retry@0.6.0
&#9474; &#9500;&#9472;&#9472; rimraf@2.2.6
&#9474; &#9500;&#9472;&#9472; semver@2.2.1
&#9474; &#9500;&#9472;&#9516; sha@1.2.3
&#9474; &#9474; &#9492;&#9472;&#9472; readable-stream@1.0.24
&#9474; &#9500;&#9472;&#9472; slide@1.1.5
&#9474; &#9500;&#9472;&#9472; tar@0.1.19
&#9474; &#9500;&#9472;&#9472; text-table@0.2.0
&#9474; &#9500;&#9472;&#9472; uid-number@0.0.3
&#9474; &#9492;&#9472;&#9472; which@1.0.5
&#9492;&#9472;&#9516; raphael-browserify@2.1.0
  &#9492;&#9472;&#9516; jsdom@0.2.19
    &#9500;&#9472;&#9516; contextify@0.1.6
    &#9474; &#9492;&#9472;&#9472; bindings@1.1.1
    &#9500;&#9472;&#9472; cssom@0.2.5
    &#9500;&#9472;&#9516; cssstyle@0.2.9
    &#9474; &#9492;&#9472;&#9472; cssom@0.3.0
    &#9500;&#9472;&#9472; htmlparser@1.7.7
    &#9492;&#9472;&#9516; request@2.33.0
      &#9500;&#9472;&#9472; aws-sign2@0.5.0
      &#9500;&#9472;&#9472; forever-agent@0.5.0
      &#9500;&#9472;&#9516; form-data@0.1.2
      &#9474; &#9500;&#9472;&#9472; async@0.2.9
      &#9474; &#9492;&#9472;&#9516; combined-stream@0.0.4
      &#9474;   &#9492;&#9472;&#9472; delayed-stream@0.0.5
      &#9500;&#9472;&#9516; hawk@1.0.0
      &#9474; &#9500;&#9472;&#9472; boom@0.4.2
      &#9474; &#9500;&#9472;&#9472; cryptiles@0.2.2
      &#9474; &#9500;&#9472;&#9472; hoek@0.9.1
      &#9474; &#9492;&#9472;&#9472; sntp@0.2.4
      &#9500;&#9472;&#9516; http-signature@0.10.0
      &#9474; &#9500;&#9472;&#9472; asn1@0.1.11
      &#9474; &#9500;&#9472;&#9472; assert-plus@0.1.2
      &#9474; &#9492;&#9472;&#9472; ctype@0.5.2
      &#9500;&#9472;&#9472; json-stringify-safe@5.0.0
      &#9500;&#9472;&#9472; mime@1.2.11
      &#9500;&#9472;&#9472; node-uuid@1.4.1
      &#9500;&#9472;&#9472; oauth-sign@0.3.0
      &#9500;&#9472;&#9472; qs@0.6.6
      &#9500;&#9472;&#9516; tough-cookie@0.12.1
      &#9474; &#9492;&#9472;&#9472; punycode@1.2.3
      &#9492;&#9472;&#9472; tunnel-agent@0.3.0
Packages: /usr/lib
&#9500;&#9472;&#9516; browserify@3.20.0
&#9474; &#9500;&#9472;&#9472; assert@1.1.0
&#9474; &#9500;&#9472;&#9516; browser-pack@2.0.1
&#9474; &#9474; &#9500;&#9472;&#9516; combine-source-map@0.3.0
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; convert-source-map@0.3.3
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; inline-source-map@0.3.0
&#9474; &#9474; &#9474; &#9492;&#9472;&#9516; source-map@0.1.31
&#9474; &#9474; &#9474;   &#9492;&#9472;&#9472; amdefine@0.1.0
&#9474; &#9474; &#9492;&#9472;&#9516; JSONStream@0.6.4
&#9474; &#9474;   &#9500;&#9472;&#9472; jsonparse@0.0.5
&#9474; &#9474;   &#9492;&#9472;&#9472; through@2.2.7
&#9474; &#9500;&#9472;&#9516; browser-resolve@1.2.2
&#9474; &#9474; &#9492;&#9472;&#9472; resolve@0.6.1
&#9474; &#9500;&#9472;&#9516; concat-stream@1.4.1
&#9474; &#9474; &#9500;&#9472;&#9516; readable-stream@1.1.10
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; core-util-is@1.0.1
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; debuglog@0.0.2
&#9474; &#9474; &#9492;&#9472;&#9472; typedarray@0.0.5
&#9474; &#9500;&#9472;&#9472; console-browserify@1.0.3
&#9474; &#9500;&#9472;&#9472; constants-browserify@0.0.1
&#9474; &#9500;&#9472;&#9472; crypto-browserify@1.0.9
&#9474; &#9500;&#9472;&#9472; deep-equal@0.1.2
&#9474; &#9500;&#9472;&#9472; defined@0.0.0
&#9474; &#9500;&#9472;&#9516; deps-sort@0.1.1
&#9474; &#9474; &#9492;&#9472;&#9516; JSONStream@0.6.4
&#9474; &#9474;   &#9500;&#9472;&#9472; jsonparse@0.0.5
&#9474; &#9474;   &#9492;&#9472;&#9472; through@2.2.7
&#9474; &#9500;&#9472;&#9472; domain-browser@1.1.1
&#9474; &#9500;&#9472;&#9472; duplexer@0.1.1
&#9474; &#9500;&#9472;&#9472; events@1.0.0
&#9474; &#9500;&#9472;&#9516; http-browserify@1.1.0
&#9474; &#9474; &#9492;&#9472;&#9472; Base64@0.2.0
&#9474; &#9500;&#9472;&#9472; https-browserify@0.0.0
&#9474; &#9500;&#9472;&#9472; inherits@2.0.1
&#9474; &#9500;&#9472;&#9516; insert-module-globals@2.3.0
&#9474; &#9474; &#9500;&#9472;&#9472; commondir@0.0.1
&#9474; &#9474; &#9500;&#9472;&#9516; lexical-scope@0.0.15
&#9474; &#9474; &#9474; &#9492;&#9472;&#9516; astw@0.0.0
&#9474; &#9474; &#9474;   &#9492;&#9472;&#9472; esprima@1.0.2
&#9474; &#9474; &#9492;&#9472;&#9472; process@0.5.2
&#9474; &#9500;&#9472;&#9516; JSONStream@0.7.1
&#9474; &#9474; &#9500;&#9472;&#9472; jsonparse@0.0.5
&#9474; &#9474; &#9492;&#9472;&#9472; through@2.2.7
&#9474; &#9500;&#9472;&#9472; minimist@0.0.5
&#9474; &#9500;&#9472;&#9516; module-deps@1.2.2
&#9474; &#9474; &#9500;&#9472;&#9516; detective@2.1.2
&#9474; &#9474; &#9474; &#9500;&#9472;&#9516; escodegen@0.0.15
&#9474; &#9474; &#9474; &#9474; &#9492;&#9472;&#9516; source-map@0.1.31
&#9474; &#9474; &#9474; &#9474;   &#9492;&#9472;&#9472; amdefine@0.1.0
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; esprima@1.0.2
&#9474; &#9474; &#9492;&#9472;&#9472; resolve@0.6.1
&#9474; &#9500;&#9472;&#9516; native-buffer-browserify@2.0.8
&#9474; &#9474; &#9500;&#9472;&#9472; base64-js@0.0.6
&#9474; &#9474; &#9492;&#9472;&#9472; ieee754@1.1.1
&#9474; &#9500;&#9472;&#9472; os-browserify@0.1.1
&#9474; &#9500;&#9472;&#9472; parents@0.0.2
&#9474; &#9500;&#9472;&#9472; path-browserify@0.0.0
&#9474; &#9500;&#9472;&#9472; punycode@1.2.3
&#9474; &#9500;&#9472;&#9472; querystring@0.2.0
&#9474; &#9500;&#9472;&#9472; shell-quote@0.0.1
&#9474; &#9500;&#9472;&#9516; stream-browserify@0.1.2
&#9474; &#9474; &#9492;&#9472;&#9472; process@0.5.2
&#9474; &#9500;&#9472;&#9472; stream-combiner@0.0.4
&#9474; &#9500;&#9472;&#9472; string_decoder@0.0.1
&#9474; &#9500;&#9472;&#9516; syntax-error@0.0.1
&#9474; &#9474; &#9492;&#9472;&#9472; esprima@0.9.9
&#9474; &#9500;&#9472;&#9472; through@2.3.4
&#9474; &#9500;&#9472;&#9516; timers-browserify@1.0.1
&#9474; &#9474; &#9492;&#9472;&#9472; process@0.5.2
&#9474; &#9500;&#9472;&#9472; tty-browserify@0.0.0
&#9474; &#9500;&#9472;&#9516; umd@2.0.0
&#9474; &#9474; &#9500;&#9472;&#9516; rfile@1.0.0
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; callsite@1.0.0
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; resolve@0.3.1
&#9474; &#9474; &#9500;&#9472;&#9516; ruglify@1.0.0
&#9474; &#9474; &#9474; &#9492;&#9472;&#9516; uglify-js@2.2.5
&#9474; &#9474; &#9474;   &#9500;&#9472;&#9516; optimist@0.3.7
&#9474; &#9474; &#9474;   &#9474; &#9492;&#9472;&#9472; wordwrap@0.0.2
&#9474; &#9474; &#9474;   &#9492;&#9472;&#9516; source-map@0.1.31
&#9474; &#9474; &#9474;     &#9492;&#9472;&#9472; amdefine@0.1.0
&#9474; &#9474; &#9492;&#9472;&#9516; uglify-js@2.4.9
&#9474; &#9474;   &#9500;&#9472;&#9472; async@0.2.9
&#9474; &#9474;   &#9500;&#9472;&#9516; optimist@0.3.7
&#9474; &#9474;   &#9474; &#9492;&#9472;&#9472; wordwrap@0.0.2
&#9474; &#9474;   &#9500;&#9472;&#9516; source-map@0.1.31
&#9474; &#9474;   &#9474; &#9492;&#9472;&#9472; amdefine@0.1.0
&#9474; &#9474;   &#9492;&#9472;&#9472; uglify-to-browserify@1.0.1
&#9474; &#9500;&#9472;&#9516; url@0.7.9
&#9474; &#9474; &#9500;&#9472;&#9472; punycode@1.0.0
&#9474; &#9474; &#9492;&#9472;&#9472; querystring@0.1.0
&#9474; &#9500;&#9472;&#9472; util@0.10.2
&#9474; &#9500;&#9472;&#9516; vm-browserify@0.0.2
&#9474; &#9474; &#9492;&#9472;&#9472; indexof@0.0.1
&#9474; &#9492;&#9472;&#9516; zlib-browserify@0.0.3
&#9474;   &#9492;&#9472;&#9516; tape@0.2.2
&#9474;     &#9500;&#9472;&#9472; deep-equal@0.0.0
&#9474;     &#9492;&#9472;&#9472; jsonify@0.0.0
&#9500;&#9472;&#9472; coffee-script@1.6.3
&#9500;&#9472;&#9516; grunt-cli@0.1.11
&#9474; &#9500;&#9472;&#9516; findup-sync@0.1.2
&#9474; &#9474; &#9500;&#9472;&#9516; glob@3.1.21
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; graceful-fs@1.2.3
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; inherits@1.0.0
&#9474; &#9474; &#9474; &#9492;&#9472;&#9516; minimatch@0.2.12
&#9474; &#9474; &#9474;   &#9500;&#9472;&#9472; lru-cache@2.5.0
&#9474; &#9474; &#9474;   &#9492;&#9472;&#9472; sigmund@1.0.0
&#9474; &#9474; &#9492;&#9472;&#9472; lodash@1.0.1
&#9474; &#9500;&#9472;&#9516; nopt@1.0.10
&#9474; &#9474; &#9492;&#9472;&#9472; abbrev@1.0.4
&#9474; &#9492;&#9472;&#9472; resolve@0.3.1
&#9500;&#9472;&#9516; less@1.5.0
&#9474; &#9500;&#9472;&#9516; clean-css@1.0.12
&#9474; &#9474; &#9492;&#9472;&#9516; commander@1.3.2
&#9474; &#9474;   &#9492;&#9472;&#9472; keypress@0.1.0
&#9474; &#9500;&#9472;&#9472; mime@1.2.11
&#9474; &#9500;&#9472;&#9472; mkdirp@0.3.5
&#9474; &#9500;&#9472;&#9516; request@2.27.0
&#9474; &#9474; &#9500;&#9472;&#9472; aws-sign@0.3.0
&#9474; &#9474; &#9500;&#9472;&#9472; cookie-jar@0.3.0
&#9474; &#9474; &#9500;&#9472;&#9472; forever-agent@0.5.0
&#9474; &#9474; &#9500;&#9472;&#9516; form-data@0.1.2
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; async@0.2.9
&#9474; &#9474; &#9474; &#9492;&#9472;&#9516; combined-stream@0.0.4
&#9474; &#9474; &#9474;   &#9492;&#9472;&#9472; delayed-stream@0.0.5
&#9474; &#9474; &#9500;&#9472;&#9516; hawk@1.0.0
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; boom@0.4.2
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; cryptiles@0.2.2
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; hoek@0.9.1
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; sntp@0.2.4
&#9474; &#9474; &#9500;&#9472;&#9516; http-signature@0.10.0
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; asn1@0.1.11
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; assert-plus@0.1.2
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; ctype@0.5.2
&#9474; &#9474; &#9500;&#9472;&#9472; json-stringify-safe@5.0.0
&#9474; &#9474; &#9500;&#9472;&#9472; node-uuid@1.4.1
&#9474; &#9474; &#9500;&#9472;&#9472; oauth-sign@0.3.0
&#9474; &#9474; &#9500;&#9472;&#9472; qs@0.6.5
&#9474; &#9474; &#9492;&#9472;&#9472; tunnel-agent@0.3.0
&#9474; &#9492;&#9472;&#9516; source-map@0.1.30
&#9474;   &#9492;&#9472;&#9472; amdefine@0.1.0
&#9500;&#9472;&#9516; npm@1.4.3
&#9474; &#9500;&#9472;&#9472; abbrev@1.0.4
&#9474; &#9500;&#9472;&#9472; ansi@0.2.1
&#9474; &#9500;&#9472;&#9472; ansicolors@0.3.2
&#9474; &#9500;&#9472;&#9472; ansistyles@0.1.3
&#9474; &#9500;&#9472;&#9472; archy@0.0.2
&#9474; &#9500;&#9472;&#9472; block-stream@0.0.7
&#9474; &#9500;&#9472;&#9472; child-process-close@0.1.1
&#9474; &#9500;&#9472;&#9472; chmodr@0.1.0
&#9474; &#9500;&#9472;&#9472; chownr@0.0.1
&#9474; &#9500;&#9472;&#9472; cmd-shim@1.1.1
&#9474; &#9500;&#9472;&#9472; columnify@0.1.2
&#9474; &#9500;&#9472;&#9472; editor@0.0.5
&#9474; &#9500;&#9472;&#9472; fstream@0.1.25
&#9474; &#9500;&#9472;&#9516; fstream-npm@0.1.6
&#9474; &#9474; &#9492;&#9472;&#9472; fstream-ignore@0.0.7
&#9474; &#9500;&#9472;&#9472; github-url-from-git@1.1.1
&#9474; &#9500;&#9472;&#9472; github-url-from-username-repo@0.0.2
&#9474; &#9500;&#9472;&#9472; glob@3.2.7
&#9474; &#9500;&#9472;&#9472; graceful-fs@2.0.2
&#9474; &#9500;&#9472;&#9472; inherits@2.0.1
&#9474; &#9500;&#9472;&#9472; ini@1.1.0
&#9474; &#9500;&#9472;&#9516; init-package-json@0.0.14
&#9474; &#9474; &#9492;&#9472;&#9472; promzard@0.2.1
&#9474; &#9500;&#9472;&#9472; lockfile@0.4.2
&#9474; &#9500;&#9472;&#9472; lru-cache@2.5.0
&#9474; &#9500;&#9472;&#9516; minimatch@0.2.14
&#9474; &#9474; &#9492;&#9472;&#9472; sigmund@1.0.0
&#9474; &#9500;&#9472;&#9472; mkdirp@0.3.5
&#9474; &#9500;&#9472;&#9472; node-gyp@0.12.2
&#9474; &#9500;&#9472;&#9472; nopt@2.2.0
&#9474; &#9500;&#9472;&#9472; npm-install-checks@1.0.0
&#9474; &#9500;&#9472;&#9472; npm-registry-client@0.4.4
&#9474; &#9500;&#9472;&#9472; npm-user-validate@0.0.3
&#9474; &#9500;&#9472;&#9516; npmconf@0.1.12
&#9474; &#9474; &#9492;&#9472;&#9516; config-chain@1.1.8
&#9474; &#9474;   &#9492;&#9472;&#9472; proto-list@1.2.2
&#9474; &#9500;&#9472;&#9472; npmlog@0.0.6
&#9474; &#9500;&#9472;&#9472; once@1.3.0
&#9474; &#9500;&#9472;&#9472; opener@1.3.0
&#9474; &#9500;&#9472;&#9472; osenv@0.0.3
&#9474; &#9500;&#9472;&#9472; path-is-inside@1.0.0
&#9474; &#9500;&#9472;&#9516; read@1.0.5
&#9474; &#9474; &#9492;&#9472;&#9472; mute-stream@0.0.4
&#9474; &#9500;&#9472;&#9472; read-installed@1.0.0
&#9474; &#9500;&#9472;&#9516; read-package-json@1.1.7
&#9474; &#9474; &#9492;&#9472;&#9472; normalize-package-data@0.2.9
&#9474; &#9500;&#9472;&#9516; request@2.30.0
&#9474; &#9474; &#9500;&#9472;&#9472; aws-sign2@0.5.0
&#9474; &#9474; &#9500;&#9472;&#9472; forever-agent@0.5.0
&#9474; &#9474; &#9500;&#9472;&#9516; form-data@0.1.2
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; async@0.2.9
&#9474; &#9474; &#9474; &#9492;&#9472;&#9516; combined-stream@0.0.4
&#9474; &#9474; &#9474;   &#9492;&#9472;&#9472; delayed-stream@0.0.5
&#9474; &#9474; &#9500;&#9472;&#9516; hawk@1.0.0
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; boom@0.4.2
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; cryptiles@0.2.2
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; hoek@0.9.1
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; sntp@0.2.4
&#9474; &#9474; &#9500;&#9472;&#9516; http-signature@0.10.0
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; asn1@0.1.11
&#9474; &#9474; &#9474; &#9500;&#9472;&#9472; assert-plus@0.1.2
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; ctype@0.5.2
&#9474; &#9474; &#9500;&#9472;&#9472; json-stringify-safe@5.0.0
&#9474; &#9474; &#9500;&#9472;&#9472; mime@1.2.11
&#9474; &#9474; &#9500;&#9472;&#9472; node-uuid@1.4.1
&#9474; &#9474; &#9500;&#9472;&#9472; oauth-sign@0.3.0
&#9474; &#9474; &#9500;&#9472;&#9472; qs@0.6.6
&#9474; &#9474; &#9500;&#9472;&#9516; tough-cookie@0.9.15
&#9474; &#9474; &#9474; &#9492;&#9472;&#9472; punycode@1.2.3
&#9474; &#9474; &#9492;&#9472;&#9472; tunnel-agent@0.3.0
&#9474; &#9500;&#9472;&#9472; retry@0.6.0
&#9474; &#9500;&#9472;&#9472; rimraf@2.2.6
&#9474; &#9500;&#9472;&#9472; semver@2.2.1
&#9474; &#9500;&#9472;&#9516; sha@1.2.3
&#9474; &#9474; &#9492;&#9472;&#9472; readable-stream@1.0.24
&#9474; &#9500;&#9472;&#9472; slide@1.1.5
&#9474; &#9500;&#9472;&#9472; tar@0.1.19
&#9474; &#9500;&#9472;&#9472; text-table@0.2.0
&#9474; &#9500;&#9472;&#9472; uid-number@0.0.3
&#9474; &#9492;&#9472;&#9472; which@1.0.5
&#9492;&#9472;&#9516; raphael-browserify@2.1.0
  &#9492;&#9472;&#9516; jsdom@0.2.19
    &#9500;&#9472;&#9516; contextify@0.1.6
    &#9474; &#9492;&#9472;&#9472; bindings@1.1.1
    &#9500;&#9472;&#9472; cssom@0.2.5
    &#9500;&#9472;&#9516; cssstyle@0.2.9
    &#9474; &#9492;&#9472;&#9472; cssom@0.3.0
    &#9500;&#9472;&#9472; htmlparser@1.7.7
    &#9492;&#9472;&#9516; request@2.33.0
      &#9500;&#9472;&#9472; aws-sign2@0.5.0
      &#9500;&#9472;&#9472; forever-agent@0.5.0
      &#9500;&#9472;&#9516; form-data@0.1.2
      &#9474; &#9500;&#9472;&#9472; async@0.2.9
      &#9474; &#9492;&#9472;&#9516; combined-stream@0.0.4
      &#9474;   &#9492;&#9472;&#9472; delayed-stream@0.0.5
      &#9500;&#9472;&#9516; hawk@1.0.0
      &#9474; &#9500;&#9472;&#9472; boom@0.4.2
      &#9474; &#9500;&#9472;&#9472; cryptiles@0.2.2
      &#9474; &#9500;&#9472;&#9472; hoek@0.9.1
      &#9474; &#9492;&#9472;&#9472; sntp@0.2.4
      &#9500;&#9472;&#9516; http-signature@0.10.0
      &#9474; &#9500;&#9472;&#9472; asn1@0.1.11
      &#9474; &#9500;&#9472;&#9472; assert-plus@0.1.2
      &#9474; &#9492;&#9472;&#9472; ctype@0.5.2
      &#9500;&#9472;&#9472; json-stringify-safe@5.0.0
      &#9500;&#9472;&#9472; mime@1.2.11
      &#9500;&#9472;&#9472; node-uuid@1.4.1
      &#9500;&#9472;&#9472; oauth-sign@0.3.0
      &#9500;&#9472;&#9472; qs@0.6.6
      &#9500;&#9472;&#9516; tough-cookie@0.12.1
      &#9474; &#9492;&#9472;&#9472; punycode@1.2.3
      &#9492;&#9472;&#9472; tunnel-agent@0.3.0

ENV:
TERM=unknown
JAVA_HOME=/usr/lib/jvm/java-7-oracle
SHLVL=1
NODE_PATH=/usr/lib/nodejs:/usr/lib/node_modules:/usr/share/javascript
XFILESEARCHPATH=/usr/dt/app-defaults/%L/Dt
SUDO_UID=1000
MAIL=/var/mail/root
PWD=/home/dl
LOGNAME=root
SUDO_USER=dl
NLSPATH=/usr/dt/lib/nls/msg/%L/%N.cat
CATALINA_BASE=/usr/share/tomcat7
LD_LIBRARY_PATH=/usr/lib/jvm/java-7-oracle/jre/lib/i386/client:/usr/lib/jvm/java-7-oracle/jre/lib/i386:
SHELL=/bin/bash
LANGUAGE=en_GB:en
SUDO_GID=1000
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
JRE_HOME=/usr/lib/jvm/java-7-oracle
APTANA_VERSION=3.4.2.1368863613
DISPLAY=:0.0
USER=root
CATALINA_HOME=/usr/share/tomcat7
HOME=/root
XAUTHORITY=/tmp/libgksu-50VWPz/.Xauthority
USERNAME=root
SUDO_COMMAND=/opt/Aptana_Studio_3.4.2/AptanaStudio3
LANG=en_GB.UTF-8



```

---

### Post by falven on 2014-05-03
Our logs are completely different in some aspects.

```

Host OS: Linux
OS Version: 3.11.0-12-generic
OS Arch: x86_64

JRE Version: 1.8.0_05
JRE Vendor: Oracle Corporation
JRE Home: /usr/lib/jvm/java-8-oracle/jre

Aptana Studio 3 Version: 3.4.2.201308081805
Install Directory: file:/usr/dev/Aptana_Studio_3/
Workspace Directory: file:/home/francisco/aptana workspace/
VM Arguments: -Xms40m
-Xmx512m
-Declipse.p2.unsignedPolicy=allow
-Declipse.log.size.max=10000
-Declipse.log.backup.max=5
-Djava.awt.headless=true
-XX:MaxPermSize=256m
-jar
/usr/dev/Aptana_Studio_3//plugins/org.eclipse.equinox.launcher_1.2.0.v20110502.jar

Language: en_US

Node.JS Version: Not installed
NPM Path: Not installed

ENV:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
XAUTHORITY=/home/francisco/.Xauthority
MANDATORY_PATH=/usr/share/gconf/default.desktop.mandatory.path
GDMSESSION=default.desktop
XDG_DATA_DIRS=/usr/share/default.desktop:/usr/share/gnome:/usr/local/share/:/usr/share/:/usr/share/mdm/
TEXTDOMAINDIR=/usr/share/locale/
XDG_CONFIG_DIRS=/etc/xdg/xdg-default.desktop:/etc/xdg
XFILESEARCHPATH=/usr/dt/app-defaults/%L/Dt
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-sNp6Ch
LANG=en_US.UTF-8
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-A6eAJInYKj,guid=12e32e536b387694f222278353658463
XDG_SESSION_ID=c1
DEFAULTS_PATH=/usr/share/gconf/default.desktop.default.path
CLUTTER_DISABLE_XINPUT=1
XDG_CURRENT_DESKTOP=GNOME
DISPLAY=:0
MDM_LANG=en_US.UTF-8
SSH_AGENT_PID=1862
USERNAME=francisco
SESSION_MANAGER=local/Frank-MINT:@/tmp/.ICE-unix/1676,unix/Frank-MINT:/tmp/.ICE-unix/1676
LOGNAME=francisco
PWD=/home/francisco
CINNAMON_VERSION=2.0.14
GDM_XSERVER_LOCATION=local
GJS_DEBUG_TOPICS=JS ERROR;JS LOG
SHELL=/bin/bash
APTANA_VERSION=3.4.2.1368863613
GIO_LAUNCHED_DESKTOP_FILE=/usr/share/applications/Aptana.desktop
GPG_AGENT_INFO=/run/user/1000/keyring-sNp6Ch/gpg:0:1
DESKTOP_SESSION=default.desktop
USER=francisco
GIO_LAUNCHED_DESKTOP_FILE_PID=3035
WINDOWPATH=8
GJS_DEBUG_OUTPUT=stderr
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
SSH_AUTH_SOCK=/run/user/1000/keyring-sNp6Ch/ssh
MDM_XSERVER_LOCATION=local
XDG_SEAT=seat0
TEXTDOMAIN=im-config
NLSPATH=/usr/dt/lib/nls/msg/%L/%N.cat
XDG_SESSION_COOKIE=16d84b83534f2a11a22ff9c1535ea382-1399161955.780404-1814462887
MDMSESSION=default.desktop
XDG_VTNR=8
XDG_RUNTIME_DIR=/run/user/1000
HOME=/home/francisco
SHLVL=1

```

---

### Post by falven on 2014-05-03
I tried it over with a fresh Ubuntu install and I get the same error message.

Would you mind posting a short quick tutorial as to how you Downloaded/Installed it?

This is the guide I follow:

[http://www.samclarke.com/2012/04/how-to-install-aptana-studio-3-on-ubuntu-12-04-lts-precise-pangolin/](http://www.samclarke.com/2012/04/how-to-install-aptana-studio-3-on-ubuntu-12-04-lts-precise-pangolin/)

Pretty sure the issue is with the installation.

---

### Post by falven on 2014-05-04
Tried it on Debian... Same ****.

Only fix I found is using the plugin instead of the standalone installation.

---

### Post by Gyokuro on 2014-05-04
Hi

I have not used Aptana (fine IDE) for a long time but I can remember that you have to install 
libjpeg62 libwebkitgtk-1.0-0

but this was requested for Aptana Studio 3. 

- HTH

---

### Post by dragonfly41 on 2014-05-04
There are two significant differences I can see ..

You are running 64bits Ubuntu I'm running 32bits Ubuntu

You are using java 8 and I'm using java 7.

Ignore the Node.js references in my log .. you don't have Node.js installed.

...

My Aptana Studio is the standalone version .. not the eclipse plugin.

My localhost web server is Apache.

...


I followed the same installation tutorial you used.

[http://www.samclarke.com/2012/04/how-to-install-aptana-studio-3-on-ubuntu-12-04-lts-precise-pangolin/](http://www.samclarke.com/2012/04/how-to-install-aptana-studio-3-on-ubuntu-12-04-lts-precise-pangolin/)

sudo unzip [name of Aptana Studio ZIP file here].zip -d /opt

wget [http://www.samclarke.com/wp-content/uploads/2012/04/AptanaStudio3.desktop](http://www.samclarke.com/wp-content/uploads/2012/04/AptanaStudio3.desktop)
sudo mv AptanaStudio3.desktop /usr/share/applications/AptanaStudio3.desktop

...

In your first post you wrote

> Have latest Sun JDK - /usr/lib/jvm/java-8-oracle Changed /usr/bin/javaxxxx symlinks to reference JDK.


But the prerequisites for Aptana are ...
[COLOR=#0000ff]sudo apt-get install openjdk-7-jdk libjpeg62 libwebkitgtk-1.0-0 git-core[/COLOR]
I'm not sure what impact java version 8 might have on Aptana running.



Your log shows ..

[COLOR=#0000ff]Host OS: Linux
OS Version: 3.11.0-12-generic
OS Arch: x86_64

JRE Version: 1.8.0_05
JRE Vendor: Oracle Corporation
JRE Home: /usr/lib/jvm/java-8-oracle/jre[/COLOR]


My log shows ...

[COLOR=#0000ff]Host OS: Linux
OS Version: 3.2.0-60-generic-pae
OS Arch: x86

JRE Version: 1.7.0_51
JRE Vendor: Oracle Corporation
JRE Home: /usr/lib/jvm/java-7-oracle/jre[/COLOR]



So I would start by installing update-java-alternatives to allow you to try switching between java 7 and 8 versions.

[http://askubuntu.com/questions/315646/update-java-alternatives-vs-update-alternatives-config-java](http://askubuntu.com/questions/315646/update-java-alternatives-vs-update-alternatives-config-java)

...

I have set in my environment variables

[COLOR=#0000ff]JAVA_HOME=/usr/lib/jvm/java-7-oracle

JRE_HOME=/usr/lib/jvm/java-7-oracle[/COLOR]

So in terminal run

[COLOR=#0000ff]echo $JAVA_HOME[/COLOR]
and
[COLOR=#0000ff]echo $JRE_HOME[/COLOR]

Do you see your correct java paths?

If not set the variables by terminal command.

...

That's all I can think of at the moment. If I can think of other clues I'll post.

Exactly what Ubuntu OS are you running?

---

### Post by dragonfly41 on 2014-05-04
Later thought ..

Have you installed 32bits or 64bits version Aptana Studio?

[http://download.cnet.com/Aptana-Studio-for-Linux-64-bit/3000-2212_4-75628484.html](http://download.cnet.com/Aptana-Studio-for-Linux-64-bit/3000-2212_4-75628484.html)

The samclarke site you referred to installs 32bits Aptana .. but it should work on 64bits Ubuntu.

Probably some library dependency is the issue.

[COLOR=maroon]

================================

Here are some more thoughts ...

Launch Aptana Studio

Go to toolbar > Windows > Preferences

general > Web Browser

default selection is "use internal web browser"

change these preferences to see if you can get an error free run
with an external browser instead of default setting  internal browser.

e.g. Use external web browser

external web browsers:     Firefox

================================

Under General > Troubleshooting

Set Debug Level = All

Select All Components to debug

================================


Under General > Web Servers

do you have Built-in
IP address 127.0.0.1
Port: 80

================================


Finally read some tips here on update-alternatives ...

[Sidenote &#8212; Install Oracle Java JRE7 and Aptana Studio 3 on Ubuntu Oneiric (11.10)]("http://nikolas.demiridis.gr/post/14666354160/install-oracle-java-jre7-and-aptana-studio-3-on-ubuntu")

[/COLOR]

---

### Post by falven on 2014-05-11
I apologize for the delay.
Finals here :/
Will post back soon with a full response.
-Falven

---


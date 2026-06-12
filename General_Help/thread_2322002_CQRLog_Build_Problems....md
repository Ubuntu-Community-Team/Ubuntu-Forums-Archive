---
title: "CQRLog Build Problems..."
date: 2016-04-25
forum: General Help
---

### Post by Patriot3G on 2016-04-25
[COLOR=#333333][FONT=Lucida Grande]Hey guys,[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I'm an Amateur Radio operator and I am trying to figure out how to build CQRLog for my Odroid C2 (running Ubuntu 16.04)...but I run into this issue where it will not compile: 

[/FONT][/COLOR]I have followed his instructions from [https://www.cqrlog.com/faq#source-code](https://www.cqrlog.com/faq#source-code)

```
[COLOR=#2E8B57][FONT=Monaco]lazbuild --ws=gtk2 --pcp=/tmp/.lazarus src/cqrlog.lpi[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]SetPrimaryConfigPath NewValue="/tmp/.lazarus" -> "/tmp/.lazarus"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]CopySecondaryConfigFile /etc/lazarus/environmentoptions.xml -> /tmp/.lazarus/env ironmentoptions.xml[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Hint: (lazarus) [RunTool] /usr/bin/fpc "-iWTOTP"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Hint: (lazarus) [RunTool] /usr/bin/fpc "-va" "compilertest.pas"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Hint: (lazarus) [RunTool] /usr/bin/fpc "-iWTOTP" "-Paarch64" "-Tlinux"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Hint: (lazarus) [RunTool] /usr/bin/fpc "-va" "-Paarch64" "-Tlinux" "compilertest .pas"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Execute Title="Compile Project, Target: cqrlog"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Working Directory="/home/patriot3g/cqrlog/src/"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Executable="/usr/bin/fpc"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[0]="-MObjFPC"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[1]="-Sghi"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[2]="-O3"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[3]="-g"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[4]="-gl"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[5]="-l"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[6]="-vewilbq"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[7]="-vn-h-"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[8]="-Fl/usr/lib/lazarus/1.6/lcl"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[9]="-Fl/opt/gnome/lib"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[10]="-Fu/home/patriot3g/cqrlog/src/lnet/lib"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[11]="-Fu/home/patriot3g/cqrlog/src/mysql"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[12]="-Fu/usr/lib/lazarus/1.6/components/turbopower_ipro/un its/aarch64-linux/gtk2"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[13]="-Fu/usr/lib/lazarus/1.6/components/tachart/lib/aarch6 4-linux/gtk2"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[14]="-Fu/usr/lib/lazarus/1.6/components/sqldb/lib/aarch64- linux/gtk2"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[15]="-Fu/usr/lib/lazarus/1.6/components/rtticontrols/lib/a arch64-linux/gtk2"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[16]="-Fu/usr/lib/lazarus/1.6/components/memds/lib/aarch64- linux/gtk2"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[17]="-Fu/usr/lib/lazarus/1.6/components/tdbf/lib/aarch64-l inux/gtk2"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[18]="-Fu/usr/lib/lazarus/1.6/components/printers/lib/aarch 64-linux/gtk2"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[19]="-Fu/usr/lib/lazarus/1.6/components/ideintf/units/aarc h64-linux/gtk2"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[20]="-Fu/usr/lib/lazarus/1.6/components/synedit/units/aarc h64-linux/gtk2"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[21]="-Fu/usr/lib/lazarus/1.6/components/sdf/lib/aarch64-li nux/gtk2"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[22]="-Fu/usr/lib/lazarus/1.6/components/lazcontrols/lib/aa rch64-linux/gtk2"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[23]="-Fu/usr/lib/lazarus/1.6/components/cairocanvas/lib/aa rch64-linux/gtk2"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[24]="-Fu/usr/lib/lazarus/1.6/lcl/units/aarch64-linux/gtk2"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[25]="-Fu/usr/lib/lazarus/1.6/lcl/units/aarch64-linux"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[26]="-Fu/usr/lib/lazarus/1.6/components/codetools/units/aa rch64-linux"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[27]="-Fu/usr/lib/lazarus/1.6/components/lazutils/lib/aarch 64-linux"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[28]="-Fu/usr/lib/lazarus/1.6/packager/units/aarch64-linux"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[29]="-Fu/home/patriot3g/cqrlog/src/"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[30]="-dLCL"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[31]="-dLCLgtk2"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[32]="-dNO_CONTEST"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Info: (lazarus) Param[33]="cqrlog.lpr"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Free Pascal Compiler version 3.0.0+dfsg-2 [2016/01/28] for aarch64[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Copyright (c) 1993-2015 by Florian Klaempfl and others[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco](1002) Target OS: Linux for AArch64[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco](3104) Compiling cqrlog.lpr[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]2 266/768 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco](3104) Compiling dLogUpload.pas[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco](3104) Compiling dData.pas[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]100 171.070/174.912 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]200 171.208/174.912 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]300 171.467/175.424 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco](3104) Compiling dUtils.pas[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]100 177.279/181.056 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]200 177.560/181.312 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]300 275.898/279.616 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]400 276.678/281.152 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]500 277.241/281.664 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]600 277.896/281.920 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]700 278.107/282.432 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(766,10) Warning: (5036) Local variable "Nu mRead" does not seem to be initialized[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(766,27) Warning: (5036) Local variable "Nu mWritten" does not seem to be initialized[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]800 278.484/282.688 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]900 278.990/283.200 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]1000 279.556/283.456 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]1100 280.007/284.224 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]1200 280.511/284.480 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]1300 280.626/284.480 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]1400 281.116/285.504 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]1500 281.635/286.272 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(1515,24) Warning: (5093) function result v ariable of a managed type does not seem to initialized[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]1600 282.176/286.528 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]1700 282.616/286.784 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]1800 282.878/286.784 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]1900 283.754/289.600 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]2000 284.084/289.856 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]2100 284.795/290.368 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(2197,26) Warning: (5089) Local variable "b efore" of a managed type does not seem to be initialized[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]2200 285.312/290.880 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]2300 285.670/290.880 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]2400 285.986/291.648 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(2431,14) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(2433,42) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(2434,18) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(2448,14) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(2451,42) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]2500 286.792/292.160 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(2522,14) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(2525,42) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]2600 287.397/292.672 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]2700 287.906/293.184 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(2666,18) Warning: (5093) function result v ariable of a managed type does not seem to initialized[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]2800 288.464/293.952 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]2900 288.595/293.952 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(2909,14) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(2911,42) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(2977,14) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(2979,42) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(2980,18) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]3000 289.334/294.464 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]3100 290.329/295.232 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(3129,13) Warning: (5066) Symbol "AppendPat hDelim" is deprecated: "Use the function in LazFileUtils unit"[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]3200 290.860/296.000 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]3300 291.400/296.512 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(3319,14) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(3322,42) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]3400 291.705/296.512 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]3500 291.937/296.512 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]3600 292.605/297.536 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]3700 293.200/298.560 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(3785,14) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(3788,42) Warning: (5043) Symbol "CommandLi ne" is deprecated[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]3800 293.931/299.328 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]3900 294.249/299.584 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]4000 294.914/300.096 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]4100 295.598/300.864 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(4195,16) Error: (4057) Can't determine whi ch overloaded function to call[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/home/patriot3g/cqrlog/src/dUtils.pas(4196,16) Error: (4057) Can't determine whi ch overloaded function to call[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]4200 296.126/301.120 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]4300 296.426/301.120 Kb Used[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]dUtils.pas(4334) Fatal: (10026) There were 2 errors compiling module, stopping[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Fatal: (1018) Compilation aborted[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Error: /usr/bin/ppca64 returned an error exitcode[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Error: (lazarus) Compile Project, Target: cqrlog: stopped with exit code 256[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ERROR: failed compiling of project /home/patriot3g/cqrlog/src/cqrlog.lpi[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Makefile:9: recipe for target 'cqrlog' failed[/FONT][/COLOR]
```


Thanks so much!!

Adam (K2AAM)

---

### Post by kc1di on 2016-04-25
Hello Adam, 
Nice to see another Ham op here.  I'm KC1DI  -- Cqrlog is available in the repositories of Ubuntu -- I would suggest installing it with the following command in a terminal.```
sudo apt-get install cqrlog
```  it's currently at version 1.9.  

I use JLog my self which is a cross platform Java Log book.  Also xlog is available in the repository. 

Let me know if I can be of further help.
It is not very often needful to build a program in Ubuntu.  

73, 
Dave Kc1di

---

### Post by Patriot3G on 2016-04-25
I've tried that route, I'm sure its because I am using an Arm64 processor...

patriot3g@odroid64:~$ sudo apt-get install cqrlog
[sudo] password for patriot3g:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 cqrlog:armhf : Depends: mysql-client:armhf but it is not installable or
                         mariadb-client:armhf but it is not installable
                Depends: libhamlib2:armhf (>= 1.2.10) but it is not going to be installed
                Depends: libhamlib-utils:armhf (>= 1.2.10) but it is not going to be installed
                Recommends: mysql-server:armhf or
                            mariadb-server:armhf but it is not installable
                Recommends: xplanet:armhf but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by kc1di on 2016-04-26
could be that the arm processor is the problem. It runs fine here on my x86_64 .
good Luck. 
Sorry can't help with the building.

---


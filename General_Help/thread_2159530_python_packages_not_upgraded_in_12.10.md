---
title: "python packages not upgraded in 12.10"
date: 2013-07-03
forum: General Help
---

### Post by Budoc on 2013-07-03
Hello,

For the past few weeks I have noticed with aptitude that 2 packages are not being upgraded with my Ubuntu 12.10 installation. These packages are: python3 and python3-minimal. If I run aptitude full-upgrade, I get the following output:

```
The following packages have unmet dependencies:
 python3-minimal : Depends: python3.2-minimal (>= 3.2.3-6ubuntu3.2) but 3.2.3-6ubuntu3.1 is installed.
 python3 : Depends: python3.2 (>= 3.2.3-6ubuntu3.2) but 3.2.3-6ubuntu3.1 is installed.
The following actions will resolve these dependencies:

       Remove the following packages:                                           
1)       apport                                                                 
2)       apport-gtk                                                             
3)       apport-hooks-medibuntu                                                 
4)       aptdaemon                                                              
5)       apturl                                                                 
6)       apturl-common                                                          
7)       bluez                                                                  
8)       bluez-alsa                                                             
9)       bluez-gstreamer                                                        
10)      checkbox                                                               
11)      checkbox-qt                                                            
12)      command-not-found                                                      
13)      firefox                                                                
14)      firefox-globalmenu                                                     
15)      firefox-gnome-support                                                  
16)      foomatic-db-compressed-ppds                                            
17)      gir1.2-ubuntuoneui-3.0                                                 
18)      gnome-bluetooth                                                        
19)      gnome-orca                                                             
20)      gnome-user-share                                                       
21)      language-selector-common                                               
22)      language-selector-gnome                                                
23)      libsyncdaemon-1.0-1                                                    
24)      libubuntuoneui-3.0-1                                                   
25)      lightdm-remote-session-uccsconfigure                                   
26)      lsb-release                                                            
27)      nautilus-share                                                         
28)      onboard                                                                
29)      openprinting-ppds                                                      
30)      printer-driver-foo2zjs                                                 
31)      printer-driver-postscript-hp                                           
32)      printer-driver-ptouch                                                  
33)      printer-driver-pxljr                                                   
34)      python-apport                                                          
35)      python3                                                                
36)      python3-apport                                                         
37)      python3-apt                                                            
38)      python3-aptdaemon                                                      
39)      python3-aptdaemon.gtk3widgets                                          
40)      python3-aptdaemon.pkcompat                                             
41)      python3-brlapi                                                         
42)      python3-cairo                                                          
43)      python3-crypto                                                         
44)      python3-dbus                                                           
45)      python3-defer                                                          
46)      python3-distupgrade                                                    
47)      python3-gdbm                                                           
48)      python3-gi                                                             
49)      python3-gi-cairo                                                       
50)      python3-httplib2                                                       
51)      python3-louis                                                          
52)      python3-lxml                                                           
53)      python3-minimal                                                        
54)      python3-oauthlib                                                       
55)      python3-pkg-resources                                                  
56)      python3-problem-report                                                 
57)      python3-pyatspi2                                                       
58)      python3-pycurl                                                         
59)      python3-software-properties                                            
60)      python3-speechd                                                        
61)      python3-update-manager                                                 
62)      python3-virtkey                                                        
63)      python3-xkit                                                           
64)      rhythmbox-ubuntuone                                                    
65)      sessioninstaller                                                       
66)      software-center                                                        
67)      software-center-aptdaemon-plugins                                      
68)      software-properties-common                                             
69)      software-properties-gtk                                                
70)      thin-client-config-agent                                               
71)      ubuntu-desktop                                                         
72)      ubuntu-drivers-common                                                  
73)      ubuntu-minimal                                                         
74)      ubuntu-release-upgrader-core                                           
75)      ubuntu-release-upgrader-gtk                                            
76)      ubuntu-standard                                                        
77)      ubuntuone-client                                                       
78)      ubuntuone-client-gnome                                                 
79)      ubuntuone-control-panel                                                
80)      ubuntuone-control-panel-qt                                             
81)      ufw                                                                    
82)      unattended-upgrades                                                    
83)      unity-lens-photos                                                      
84)      unity-scope-gdocs                                                      
85)      unity-scope-musicstores                                                
86)      update-manager                                                         
87)      update-manager-core                                                    
88)      update-notifier                                                        
89)      xdiagnose                                                              
90)      xul-ext-ubufox                                                         
91)      xul-ext-unity                                                          
92)      xul-ext-websites-integration                                           

       Leave the following dependencies unresolved:                             
93)      apport-symptoms recommends apport                                      
94)      brltty recommends python3                                              
95)      foomatic-db-engine recommends foomatic-db-compressed-ppds | foomatic-db
96)      friendly-recovery recommends update-manager-core (>= 0.90.0)           
97)      hplip recommends printer-driver-postscript-hp                          
98)      indicator-session recommends packagekit-system-interface | packagekit  
99)      kerneloops-daemon recommends apport                                    
100)     libpackagekit-glib2-14 recommends packagekit-system-interface | package
101)     oneconf recommends software-center (>= 4.1.21)                         
102)     oneconf recommends update-notifier (>= 0.103)                          
103)     printer-driver-min12xxw recommends foomatic-db-compressed-ppds | foomat
104)     ubuntu-desktop recommends nautilus-share                               
105)     ubuntu-desktop recommends onboard                                      
106)     ubuntu-desktop recommends printer-driver-foo2zjs                       
107)     ubuntu-desktop recommends printer-driver-ptouch                        
108)     ubuntu-desktop recommends printer-driver-pxljr                         
109)     ubuntu-standard recommends command-not-found                           
110)     unity-lens-music recommends unity-scope-musicstores                    
111)     update-notifier recommends software-properties-gtk                     
112)     synaptic recommends software-properties-gtk                            
113)     apport-gtk recommends update-notifier                                  
114)     deja-dup recommends ubuntuone-client                                   
115)     deja-dup recommends ubuntuone-control-panel                            
116)     file-roller recommends sessioninstaller | packagekit                   
117)     firefox recommends xul-ext-ubufox                                      
118)     python-apport recommends apport                                        
119)     python-apt recommends lsb-release                                      
120)     python-aptdaemon recommends aptdaemon                                  
121)     python3-apport recommends apport                                       
122)     python3-aptdaemon recommends aptdaemon                                 
123)     remote-login-service recommends thin-client-config-agent               
124)     rhythmbox-mozilla recommends firefox | epiphany-browser | www-browser  
125)     software-center recommends software-properties-gtk                     
126)     software-center recommends sessioninstaller                            
127)     ubuntu-drivers-common recommends python3-aptdaemon.pkcompat            
128)     unity recommends unity-lens-photos                                     
129)     unity-greeter recommends lightdm-remote-session-uccsconfigure          
130)     unity-lens-files recommends unity-scope-gdocs                          
131)     update-manager recommends software-properties-gtk (>= 0.71.2)          


Accept this solution? [Y/n/q/?] 

```

A lot of changes to be made! I have not run a full-upgrade in the hope that whatever is causing this problem is resolved, but it has been a few weeks now and I am keen to understand why this is happening, and how to fix it. 

I've looked at the problem further, and I found that I do not have the updated version of python3.2-minimal installed:

```
aptitude versions python3.2-minimal                      [17:41:29]
Package python3.2-minimal:                        
p   3.2.3-6ubuntu3                                quantal                   500 
i   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 

Package python3.2-minimal:i386:
p   3.2.3-6ubuntu3                                quantal                   500 
p   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 
```

However, I cannot install the latest version:

```
 sudo aptitude install python3.2-minimal=3.2.3-6ubuntu.3.2                   [17:44:12]
Unable to find a version "3.2.3-6ubuntu.3.2" for the package "python3.2-minimal"
Unable to find a version "3.2.3-6ubuntu.3.2" for the package "python3.2-minimal"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```

I've also tried aptitude reinstall python3.2-minimal, but the older package is reinstalled.

Similarly with python3.2:

```
aptitude versions python3.2                              [17:44:47]
Package idle-python3.2:                   
p   3.2.3-6ubuntu3                                quantal                   500 
p   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 

Package libpython3.2:
p   3.2.3-6ubuntu3                                quantal                   500 
i   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 

Package libpython3.2:i386:
p   3.2.3-6ubuntu3                                quantal                   500 
p   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 

Package python3.2:
p   3.2.3-6ubuntu3                                quantal                   500 
i   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 

Package python3.2-dbg:
p   3.2.3-6ubuntu3                                quantal                   500 
p   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 

Package python3.2-dbg:i386:
p   3.2.3-6ubuntu3                                quantal                   500 
p   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 

Package python3.2-dev:
p   3.2.3-6ubuntu3                                quantal                   500 
p   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 

Package python3.2-dev:i386:
p   3.2.3-6ubuntu3                                quantal                   500 
p   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 

Package python3.2-doc:
p   3.2.3-6ubuntu3                                quantal                   500 
p   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 

Package python3.2-examples:
p   3.2.3-6ubuntu3                                quantal                   500 
p   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 

Package python3.2-minimal:
p   3.2.3-6ubuntu3                                quantal                   500 
i   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 

Package python3.2-minimal:i386:
p   3.2.3-6ubuntu3                                quantal                   500 
p   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 

Package python3.2:i386:
p   3.2.3-6ubuntu3                                quantal                   500 
p   3.2.3-6ubuntu3.1                              quantal-security          990 
p   3.2.3-6ubuntu3.2                              quantal-updates           900 

```

```
ai python3.2=3.2.3-6ubuntu3.2                            [17:49:50]
The following packages will be upgraded: 
  python3.2{b} 
1 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 2,585 kB of archives. After unpacking 0 B will be used.
The following packages have unmet dependencies:
 libpython3.2 : Depends: python3.2 (= 3.2.3-6ubuntu3.1) but 3.2.3-6ubuntu3.2 is to be installed.
 python3.2 : Depends: python3.2-minimal (= 3.2.3-6ubuntu3.2) but 3.2.3-6ubuntu3.1 is installed.
The following actions will resolve these dependencies:

       Remove the following packages:                                           
1)       apport                                                                 
2)       apport-gtk                                                             
3)       apport-hooks-medibuntu                                                 
4)       aptdaemon                                                              
5)       apturl                                                                 
6)       apturl-common                                                          
7)       bluez                                                                  
8)       bluez-alsa                                                             
9)       bluez-gstreamer                                                        
10)      checkbox                                                               
11)      checkbox-qt                                                            
12)      command-not-found                                                      
13)      deja-dup                                                               
14)      eog                                                                    
15)      firefox                                                                
16)      firefox-globalmenu                                                     
17)      firefox-gnome-support                                                  
18)      foomatic-db-compressed-ppds                                            
19)      gedit                                                                  
20)      gir1.2-peas-1.0                                                        
21)      gir1.2-rb-3.0                                                          
22)      gir1.2-totem-1.0                                                       
23)      gir1.2-ubuntuoneui-3.0                                                 
24)      gnome-bluetooth                                                        
25)      gnome-orca                                                             
26)      gnome-user-share                                                       
27)      language-selector-common                                               
28)      language-selector-gnome                                                
29)      libpeas-1.0-0                                                          
30)      libpython3.2                                                           
31)      librhythmbox-core6                                                     
32)      libsyncdaemon-1.0-1                                                    
33)      libtotem0                                                              
34)      libubuntuoneui-3.0-1                                                   
35)      lightdm-remote-session-uccsconfigure                                   
36)      lsb-release                                                            
37)      nautilus-share                                                         
38)      onboard                                                                
39)      openprinting-ppds                                                      
40)      printer-driver-foo2zjs                                                 
41)      printer-driver-postscript-hp                                           
42)      printer-driver-ptouch                                                  
43)      printer-driver-pxljr                                                   
44)      python-apport                                                          
45)      python3                                                                
46)      python3-apport                                                         
47)      python3-apt                                                            
48)      python3-aptdaemon                                                      
49)      python3-aptdaemon.gtk3widgets                                          
50)      python3-aptdaemon.pkcompat                                             
51)      python3-brlapi                                                         
52)      python3-cairo                                                          
53)      python3-crypto                                                         
54)      python3-dbus                                                           
55)      python3-defer                                                          
56)      python3-distupgrade                                                    
57)      python3-gdbm                                                           
58)      python3-gi                                                             
59)      python3-gi-cairo                                                       
60)      python3-httplib2                                                       
61)      python3-louis                                                          
62)      python3-lxml                                                           
63)      python3-oauthlib                                                       
64)      python3-pkg-resources                                                  
65)      python3-problem-report                                                 
66)      python3-pyatspi2                                                       
67)      python3-pycurl                                                         
68)      python3-software-properties                                            
69)      python3-speechd                                                        
70)      python3-update-manager                                                 
71)      python3-virtkey                                                        
72)      python3-xkit                                                           
73)      python3.2                                                              
74)      rhythmbox                                                              
75)      rhythmbox-mozilla                                                      
76)      rhythmbox-plugin-cdrecorder                                            
77)      rhythmbox-plugin-magnatune                                             
78)      rhythmbox-plugin-zeitgeist                                             
79)      rhythmbox-plugins                                                      
80)      rhythmbox-ubuntuone                                                    
81)      sessioninstaller                                                       
82)      software-center                                                        
83)      software-center-aptdaemon-plugins                                      
84)      software-properties-common                                             
85)      software-properties-gtk                                                
86)      thin-client-config-agent                                               
87)      totem                                                                  
88)      totem-mozilla                                                          
89)      totem-plugins                                                          
90)      ubuntu-desktop                                                         
91)      ubuntu-drivers-common                                                  
92)      ubuntu-minimal                                                         
93)      ubuntu-release-upgrader-core                                           
94)      ubuntu-release-upgrader-gtk                                            
95)      ubuntu-standard                                                        
96)      ubuntuone-client                                                       
97)      ubuntuone-client-gnome                                                 
98)      ubuntuone-control-panel                                                
99)      ubuntuone-control-panel-qt                                             
100)     ufw                                                                    
101)     unattended-upgrades                                                    
102)     unity-lens-photos                                                      
103)     unity-scope-gdocs                                                      
104)     unity-scope-musicstores                                                
105)     update-manager                                                         
106)     update-manager-core                                                    
107)     update-notifier                                                        
108)     xdiagnose                                                              
109)     xul-ext-ubufox                                                         
110)     xul-ext-unity                                                          
111)     xul-ext-websites-integration                                           

       Leave the following dependencies unresolved:                             
112)     apport-symptoms recommends apport                                      
113)     brltty recommends python3                                              
114)     foomatic-db-engine recommends foomatic-db-compressed-ppds | foomatic-db
115)     friendly-recovery recommends update-manager-core (>= 0.90.0)           
116)     hplip recommends printer-driver-postscript-hp                          
117)     indicator-session recommends packagekit-system-interface | packagekit  
118)     kerneloops-daemon recommends apport                                    
119)     libpackagekit-glib2-14 recommends packagekit-system-interface | package
120)     oneconf recommends software-center (>= 4.1.21)                         
121)     oneconf recommends update-notifier (>= 0.103)                          
122)     printer-driver-min12xxw recommends foomatic-db-compressed-ppds | foomat
123)     unity-lens-music recommends unity-scope-musicstores                    
124)     update-notifier recommends software-properties-gtk                     
125)     synaptic recommends software-properties-gtk                            
126)     apport-gtk recommends update-notifier                                  
127)     deja-dup recommends ubuntuone-client                                   
128)     deja-dup recommends ubuntuone-control-panel                            
129)     file-roller recommends sessioninstaller | packagekit                   
130)     firefox recommends xul-ext-ubufox                                      
131)     gedit-common recommends gedit                                          
132)     python-apport recommends apport                                        
133)     python-apt recommends lsb-release                                      
134)     python-aptdaemon recommends aptdaemon                                  
135)     python3-apport recommends apport                                       
136)     python3-aptdaemon recommends aptdaemon                                 
137)     remote-login-service recommends thin-client-config-agent               
138)     rhythmbox-data recommends rhythmbox                                    
139)     rhythmbox-mozilla recommends firefox | epiphany-browser | www-browser  
140)     software-center recommends software-properties-gtk                     
141)     software-center recommends sessioninstaller                            
142)     ubuntu-drivers-common recommends python3-aptdaemon.pkcompat            
143)     unity recommends unity-lens-photos                                     
144)     unity-greeter recommends lightdm-remote-session-uccsconfigure          
145)     unity-lens-files recommends unity-scope-gdocs                          
146)     update-manager recommends software-properties-gtk (>= 0.71.2)          
147)     python3.2-minimal recommends python3.2                                 


Accept this solution? [Y/n/q/?] 

```

I haven't had any troublesome updates before this, so I'm a bit of a loss as to why this has happened. Any help at getting out of this trouble would be most appreciated! Attached is a list of ppas that I have installed.

---

### Post by Cheesehead on 2013-07-04
Looks like a classic case of PPA pollution.

Try disabling all PPAs and try updating again.
Alternately, look into each PPA until you find the appropriate Python packages, remove that application and dependencies, disable that PPA, and try updating again.

---


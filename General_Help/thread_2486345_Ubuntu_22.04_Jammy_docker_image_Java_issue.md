---
title: "Ubuntu 22.04 Jammy docker image Java issue"
date: 2023-04-26
forum: General Help
---

### Post by bharanitharan on 2023-04-26
I'm using ubuntu docker image and I upgraded from focal to Jammy. After upgrade to Jammy, I see an issue in executing Java commands, see below,

```

$ docker -v                                                                                                                                                                                                           
Docker version 19.03.12, build 48a66213fe                                                                                                                                                                                                    
$                                                                                                                                                                                                                     
$ docker run -it jammy-20230126-jre:0.1 /bin/bash                                                                                                                                                                     
root@9eea578b4e8b:/#                                                                                                                                                                                                                         
root@9eea578b4e8b:/# java -version                                                                                                                                                                                                           
#                                                                                                                                                                                                                                            
# There is insufficient memory for the Java Runtime Environment to continue.                                                                                                                                                                 
# Cannot create GC thread. Out of system resources.                                                                                                                                                                                          
# An error report file with more information is saved as:                                                                                                                                                                                    
# //hs_err_pid7.log                                                                                                                                                                                                                          
root@9eea578b4e8b:/# 


```

This issue is not there upgraded docker engine,
```

$ docker -v                                                                                                                                                                                            
Docker version 23.0.3, build 3e7cbfd                                                                                                                                                                                                         
$                                                                                                                                                                                                      
$ docker run -it jammy-20230126-jre:0.1 /bin/bash                                                                                                                                                      
root@f7f143227d15:/# java -version                                                                                                                                                                                                           
openjdk version "1.8.0_322"                                                                                                                                                                                                                  
OpenJDK Runtime Environment (Zulu 8.60.0.21-CA-linux64) (build 1.8.0_322-b06)                                                                                                                                                                
OpenJDK 64-Bit Server VM (Zulu 8.60.0.21-CA-linux64) (build 25.322-b06, mixed mode)                                                                                                                                                          
root@f7f143227d15:/#


```

Not sure in the first case if the issue is actually because of the memory issue, since it is a version command, Its may be failing for some other issue but the error shows as "[COLOR=#BBBBBB][FONT=&amp]insufficient memory for the Java Runtime Environment to continue[/FONT][/COLOR]"

Are there any compatibility issue between Jammy and the docker engines while using Java?

---


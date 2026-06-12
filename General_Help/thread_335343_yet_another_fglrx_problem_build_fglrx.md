---
title: "yet another fglrx problem build fglrx"
date: 2007-01-10
forum: General Help
---

### Post by japser on 2007-01-10
after i follow install instructions  here [http://http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually")

then i tried to 
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

i got this error  when i tried to build fglrx:
Build of the package fglrx-kernel-src failed! How do you wish to proceed?

```
							dh_testroot                                                               
                                                &#9474; rm -f configure-stamp 
                                                &#9474; rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a 
                                                &#9474; rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd 
                                                &#9474; rm -rf .tmp_versions  
                                                &#9474; rm -rf patch 
                                                &#9474; dh_clean 
                                                &#9474; rm /usr/src/modules/fglrx/debian/control  
                                                &#9474; rm /usr/src/modules/fglrx/debian/dirs 
                                                &#9474; debian/rules:41: *** the unpacked source (8.32.5-1) doesn't match the
                                                &#9474; fglrx-kernel-source package (8.32.5+2.6.20.1-6)  
                                                &#9474; debian/rules:42: *** if this is not what you want, erase 
                                                &#9474; /usr/src/modules/fglrx and start over
                                                &#9474; if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \    
                                                &#9474;         cat /usr/src/modules/fglrx/debian/control.template > 
                                                /usr/src/modules/fglrx/debian/control; \                                  
                                                &#9474;         fi                                                        
                                                &#9474; if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \ 
                                                &#9474;         mv /usr/src/modules/fglrx/debian/postinst 
                                                &#9474; /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.20-1-generic.postinst; \   
                                                &#9474;         fi 
                                                &#9474; dh_testdir  
                                                &#9474; touch configure-stamp 
                                                &#9474; dh_testdir  
                                                &#9474; /usr/bin/make -C /lib/modules/2.6.20-1-generic/build  
                                                &#9474; SUBDIRS=/usr/src/modules/fglrx modules  
                                                &#9474; make[1]: Entering directory `/usr/src/linux-headers-2.6.20-1-generic' 
                                                &#9474;   CC [M]  /usr/src/modules/fglrx/firegl_public.o
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:189: error: expected declaration  
                                                &#9474; specifiers or ‘...’ before ‘mlock’                  
                                                  /usr/src/modules/fglrx/firegl_public.c:189: error: expected declaration    
                                                &#9474; specifiers or ‘...’ before ‘addr’  
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:189: error: expected declaration   
                                                &#9474; specifiers or ‘...’ before ‘len’    
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:191: warning: return type  
                                                &#9474; defaults to ‘int’                                                          &#9618;
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c: In function ‘_syscall2’: 
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:191: error: expected declaration 
                                                &#9474; specifiers before ‘_syscall2’    
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:224: error: parameter 
                                                &#9474; ‘__ke_debuglevel’ is initialized 
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:225: error: parameter  
                                                &#9474; ‘__ke_moduleflags’ is initialized  
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:228: error: storage class 
                                                &#9474; specified for parameter ‘__mod_author228’  
                                                /usr/src/modules/fglrx/firegl_public.c:229: error: storage class  
                                                &#9474; specified for parameter ‘__mod_description229’   
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:229: error: parameter
                                                &#9474; ‘__mod_description229’ is initialized   
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:229: warning: ‘__used__’   
                                                &#9474; attribute ignored  
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:229: error: section attribute not  
                                                &#9474; allowed for ‘__mod_description229’  
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:233: error: expected ‘=’, ‘,’,  
                                                &#9474; ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token 
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:233: error: expected declaration   
                                                &#9474; specifiers before ‘;’ token   
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:233: error: storage class  
                                                &#9474; specified for parameter ‘__param_perm_check_firegl’  
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:233: error: parameter   
                                                ‘__param_perm_check_firegl’ is initialized  
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:233: error: storage class    
                                                &#9474; specified for parameter ‘__param_str_firegl’ 
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:233: error: parameter  
                                                &#9474; ‘__param_str_firegl’ is initialized  
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:233: error: storage class 
                                                &#9474; specified for parameter ‘__param_firegl’  
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:233: error: parameter  
                                                &#9474; ‘__param_firegl’ is initialized   
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:233: warning: ‘__used__’   
                                                &#9474; attribute ignored    
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:233: error: section attribute not   
                                                &#9474; allowed for ‘__param_firegl’  
                                                &#9474; /usr/src/modules/fglrx/firegl_public.c:233: error: alignment may not be  
                                                &#9474; specified for ‘__param_firegl’ 
                                                
                                                ETCETC      
```

can anyone help me?

---

### Post by Renji03 on 2007-01-10
Hey, I also installed fglrx using that guide.  I had the same problem as you along the way but I somehow skipped over the "Install the .deb packages".  So when I tried building it I got that error.

Not sure if this helps at all but I can attest to the fact that the guide you used does indeed work.

---

### Post by japser on 2007-01-10
I didn't skip it. I  installed the  *.deb packages and adapt updater comes to live with fglrx updates after the failed build i installed these updates but still fglrx doesn't work....

---


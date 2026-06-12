---
title: "broken packages"
date: 2007-02-17
forum: General Help
---

### Post by who_cares on 2007-02-17
I'm trying re-install ejabberd on ubuntu 6.10 server because right now it exits with this:
```
Kernel pid terminated (application_controller) ({application_start_failure,kernel,{shutdown,{kernel,start,[normal,[]]}}})
```

I tried "apt-get remove ejabberd" but that returns this:
```
dpkg: serious warning: files list file for package `eject' missing, assuming package has no files currently installed.
```
and that is followed by:
```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

any ideas on how to get that eject file list (if that's even what I need to fix this)?

---

### Post by who_cares on 2007-02-17
bump

---

### Post by who_cares on 2007-02-19
one more bump

---

### Post by who_cares on 2007-02-21
bump

---

### Post by yusufk on 2007-02-27
I've got the same problem, can't get it to work, can't uninstall it, very frustrating!

```
 sudo apt-get remove ejabberd 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ejabberd
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ejabberd
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
Need to get 0B of archives.
After unpacking 2310kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 119061 files and directories currently installed.)
Removing ejabberd ...
Can't store backup in "/var/tmp/ejabberd-database.okWelp2614" at node ejabberd@fld23270: {"Cannot prepare checkpoint (replica not available)",
                                                                                          [config,
                                                                                           {{1172,
                                                                                             571297,
                                                                                             149261},
                                                                                            ejabberd@fld23270}]}
dpkg: error processing ejabberd (--remove):
 subprocess pre-removal script returned error exit status 1
Starting jabber server: ejabberd.
Errors were encountered while processing:
 ejabberd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
```

sudo ejabberd
Password:
{error_logger,{{2007,2,27},{12,32,37}},"Protocol: ~p: register error: ~p~n",["inet_tcp",{{badmatch,{error,duplicate_name}},[{inet_tcp_dist,listen,1},{net_kernel,start_protos,4},{net_kernel,start_protos,3},{net_kernel,init_node,2},{net_kernel,init,1},{gen_server,init_it,6},{proc_lib,init_p,5}]}]}
{error_logger,{{2007,2,27},{12,32,37}},crash_report,[[{pid,<0.21.0>},{registered_name,net_kernel},{error_info,{error,badarg}},{initial_call,{gen,init_it,[gen_server,<0.18.0>,<0.18.0>,{local,net_kernel},net_kernel,{ejabberd,shortnames,15000},[]]}},{ancestors,[net_sup,kernel_sup,<0.8.0>]},{messages,[]},{links,[#Port<0.9>,<0.18.0>]},{dictionary,[{longnames,false}]},{trap_exit,true},{status,running},{heap_size,377},{stack_size,21},{reductions,408}],[]]}
{error_logger,{{2007,2,27},{12,32,37}},supervisor_report,[{supervisor,{local,net_sup}},{errorContext,start_error},{reason,{'EXIT',nodistribution}},{offender,[{pid,undefined},{name,net_kernel},{mfa,{net_kernel,start_link,[[ejabberd,shortnames]]}},{restart_type,permanent},{shutdown,2000},{child_type,worker}]}]}
{error_logger,{{2007,2,27},{12,32,37}},supervisor_report,[{supervisor,{local,kernel_sup}},{errorContext,start_error},{reason,shutdown},{offender,[{pid,undefined},{name,net_sup},{mfa,{erl_distribution,start_link,[]}},{restart_type,permanent},{shutdown,infinity},{child_type,supervisor}]}]}
{error_logger,{{2007,2,27},{12,32,37}},crash_report,[[{pid,<0.7.0>},{registered_name,[]},{error_info,{shutdown,{kernel,start,[normal,[]]}}},{initial_call,{application_master,init,[<0.5.0>,<0.6.0>,{appl_data,kernel,[application_controller,erl_reply,auth,boot_server,code_server,disk_log_server,disk_log_sup,erl_prim_loader,error_logger,file_server,file_server_2,fixtable_server,global_group,global_name_server,heart,init,kernel_config,kernel_sup,net_kernel,net_sup,rex,user,os_server,ddll_server,erl_epmd,inet_db,pg2],undefined,{kernel,[]},[application,application_controller,application_master,application_starter,auth,code,code_aux,packages,code_server,dist_util,erl_boot_server,erl_distribution,erl_prim_loader,erl_reply,erlang,error_handler,error_logger,file,file_server,old_file_server,file_io_server,prim_file,global,global_group,global_search,group,heart,hipe_unified_loader,inet6_tcp,inet6_tcp_dist,inet6_udp,inet_config,inet_hosts,inet_gethost_native,inet_tcp_dist,init,kernel,kernel_config,net,net_adm,net_kernel,os,ram_file,rpc,user,user_drv,user_sup,disk_log,disk_log_1,disk_log_server,disk_log_sup,dist_ac,erl_ddll,erl_epmd,erts_debug,gen_tcp,gen_udp,prim_inet,inet,inet_db,inet_dns,inet_parse,inet_res,inet_tcp,inet_udp,pg2,seq_trace,wrap_log_reader,zlib,otp_ring0],[],infinity,infinity},normal]}},{ancestors,[<0.6.0>]},{messages,[{'EXIT',<0.8.0>,normal}]},{links,[<0.6.0>,<0.5.0>]},{dictionary,[]},{trap_exit,true},{status,running},{heap_size,987},{stack_size,21},{reductions,2063}],[]]}
{error_logger,{{2007,2,27},{12,32,37}},std_info,[{application,kernel},{exited,{shutdown,{kernel,start,[normal,[]]}}},{type,permanent}]}
{"Kernel pid terminated",application_controller,"{application_start_failure,kernel,{shutdown,{kernel,start,[normal,[]]}}}"}

Crash dump was written to: erl_crash.dump
Kernel pid terminated (application_controller) ({application_start_failure,kernel,{shutdown,{kernel,start,[normal,[]]}}})

```

---

### Post by yusufk on 2007-02-27
Ok, so now I've managed to remove it using this:

[http://ubuntuforums.org/showpost.php?p=1967059&postcount=5](http://ubuntuforums.org/showpost.php?p=1967059&postcount=5)

and it seems one needs erlang r10 to run ejabberd, which sucks.

---


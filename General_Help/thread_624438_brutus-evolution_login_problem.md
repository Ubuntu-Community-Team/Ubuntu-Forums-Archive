---
title: "brutus-evolution login problem"
date: 2007-11-26
forum: General Help
---

### Post by ip-rob on 2007-11-26
I've set up the following environment:



Ubuntu Gutsy (7.10)

Evolution 2.12

Exchange-brutus (download deb package for Fiesty, 1.1.27.4) Brutus server (0.9.36.1) on a Windows 2003 server



I'm able to configure the brutus connector and am using IP addresses just to make sure I'm not having DNS issues.  I can ping the brutus server on my Windows box from the Gutsy machine without a problem.  I've also tested MAPI connectivity on the Windows box using the mapi tools at 42tools.com site.



When I launch Evolution I get the message "Error while scanning folders".  I set up the debug option in a terminal window on my ubuntu client and captured the debug logs.  Here is that log.  Any help to get logged in would be great as I'd love to try out this connector on my Exchange 2007 environment.



** (evolution:11371): DEBUG: mailto URL command: evolution %s

** (evolution:11371): DEBUG: mailto URL program: evolution

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - camel_provider_module_init() in camel-brutus-provider.c@272: Brutus provider startup

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - camel_provider_module_init() in camel-brutus-provider.c@299: WARNING: Can not get exclusive lock on brutusd lock file

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - camel_provider_module_init() in camel-brutus-provider.c@318: "system(brutus-keyringd)" returned EXIT_SUCCESS

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - camel_brutus_store_class_init() in camel-brutus-store.c@1929: 

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - camel_brutus_store_init() in camel-brutus-store.c@3667: 

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_construct() in camel-brutus-store.c@1978: 

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_construct() in camel-brutus-store.c@2116: Initializing CORBA

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_orb_init() in camel-brutus-store.c@1778: 

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_orb_init() in camel-brutus-store.c@1792: Invoking ORB_Init()

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_orb_init() in camel-brutus-store.c@1815: Getting root POA

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_orb_init() in camel-brutus-store.c@1837: The ORB is initialized

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_construct() in camel-brutus-store.c@2150: Getting root POAManager, activating the RootPOA and instantiating the lifeline

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_construct() in camel-brutus-store.c@2212: priv->lifeline.filling created

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_construct() in camel-brutus-store.c@2215: Using local network capable Brutus proxy

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_construct() in camel-brutus-store.c@2235: Testing primary BrutusCheck object...

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_construct() in camel-brutus-store.c@2249: priv->lifeline.filling - OK

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_construct() in camel-brutus-store.c@2252: Testing BrutusCheck object wrapper...

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - camel-brutus-store.c@2263: System Exception : IDL:omg.org/CORBA/COMM_FAILURE:1.0

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_construct() in camel-brutus-store.c@2264: priv->lifeline.wrapper - Exception caught: Evolution shell not up?

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_construct() in camel-brutus-store.c@2309: 

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - delayed_free_thread_func() in camel-brutus-store.c@162: 

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_get_folder_info() in camel-brutus-store.c@3464: (null)

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_get_folder_info() in camel-brutus-store.c@3467: (null)

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_mapi_shutdown() in camel-brutus-store.c@1696: 

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_connect() in camel-brutus-store.c@2416: Attempting to query a session from the proxy

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_connect() in camel-brutus-store.c@2424: xxxxxxxxx (replaced this with x's - Rob)

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_connect() in camel-brutus-store.c@2425: xxxxxxxxx (replaced this with x's - Rob)

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_connect() in camel-brutus-store.c@2471: Could not get session from proxy, must log on explicitly

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:07 2007) - brutus_connect() in camel-brutus-store.c@2480: No stored MAPI Profile - generating a new one

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_connect() in camel-brutus-store.c@2490: Using this MAPI Profile: "8468e6cb-24e8-4887-b5ca-f0b994c89b78"

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_connect() in camel-brutus-store.c@2492: Getting reference to BrutusLogOn object

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_connect() in camel-brutus-store.c@2506: Could not resolve (resolve_initial_references) BrutusLogOn, falling back to corbaloc...

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_connect() in camel-brutus-store.c@2526: BrutusLogOn resolved

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_connect() in camel-brutus-store.c@2528: BrutusLogOn reference has been acquired

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_connect() in camel-brutus-store.c@2530: 

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_connect() in camel-brutus-store.c@2654: Could not connect to Brutus server

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_connect() in camel-brutus-store.c@2660: No IMAPISession offer - releasing query lock

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_connect() in camel-brutus-store.c@2681: 

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_connect() in camel-brutus-store.c@2685: 

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_connect() in camel-brutus-store.c@2733: 

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_build_folder_tree_from_cache() in camel-brutus-store.c@1522: 

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_get_from_fi_cache() in camel-brutus-store.c@572: 151fc34dc5867502fc0bc11b15207401

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_folder_info_free() in camel-brutus-store.c@800: 

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_folder_info_free() in camel-brutus-store.c@800: 

** BRUTUS 1.1.27.4 (Fri Nov 23 21:22:08 2007) - brutus_folder_info_free() in camel-brutus-store.c@800: 



Here is what the server log shows:

#16

Severity          : *** LEADING LOG ENTRY ***

UTC time          : Fri Nov 23 21:20:51 2007

Mark              : From a Log:: class instance

Brutus server     : xxxxx(replaced by Rob)

Windows domain    : xxxxx (replaced by Rob)

Domain dontroller : xxxxx (replaced by Rob)

Brutus version    : Brutus Server 0.9.36.1

MAPI version      : Microsoft Exchange 6.5

Process ID        : 544

File              : ..\servant_impl\BrutusLogOnS_impl.cpp

Line              : 242

Message           : Log entry header



#17

Severity          : INFORMATION

UTC time          : Fri Nov 23 21:20:51 2007

Mark              : From a Log:: class instance

Brutus server     : xxxxx (replaced by Rob)

Windows domain    : xxxxx (replaced by Rob)

Domain controller : xxxxx (replaced by Rob)

Brutus version    : Brutus Server 0.9.36.1

MAPI version      : Microsoft Exchange 6.5

Process ID        : 544

File              : ..\servant_impl\BrutusLogOnS_impl.cpp

Line              : 243

Following         : #16

Message           : Entering BRUTUS_BrutusLogOn_i::GetVersion()



#18

Severity          : INFORMATION

UTC time          : Fri Nov 23 21:20:51 2007

Mark              : From a Log:: class instance

Brutus server     : xxxxx (replaced by Rob)

Windows domain    : xxxxx (replaced by Rob)

Domain controller : xxxxx (replaced by Rob)

Brutus version    : Brutus Server 0.9.36.1

MAPI version      : Microsoft Exchange 6.5

Process ID        : 544

File              : ..\servant_impl\BrutusLogOnS_impl.cpp

Line              : 261

Following         : #16

Message           : Leaving BRUTUS_BrutusLogOn_i::GetVersion()



#19

Severity          : *** LEADING LOG ENTRY ***

UTC time          : Fri Nov 23 21:22:05 2007

Mark              : From a Log:: class instance

Brutus server     : xxxxx (replaced by Rob)

Windows domain    : xxxxx (replaced by Rob)

Domain dontroller : xxxxx (replaced by Rob)

Brutus version    : Brutus Server 0.9.36.1

MAPI version      : Microsoft Exchange 6.5

Process ID        : 544

File              : ..\servant_impl\BrutusLogOnS_impl.cpp

Line              : 242

Message           : Log entry header



#20

Severity          : INFORMATION

UTC time          : Fri Nov 23 21:22:05 2007

Mark              : From a Log:: class instance

Brutus server     : xxxxx (replaced by Rob)

Windows domain    : xxxxx (replaced by Rob)

Domain controller : xxxxx (replaced by Rob)

Brutus version    : Brutus Server 0.9.36.1

MAPI version      : Microsoft Exchange 6.5

Process ID        : 544

File              : ..\servant_impl\BrutusLogOnS_impl.cpp

Line              : 243

Following         : #19

Message           : Entering BRUTUS_BrutusLogOn_i::GetVersion()



#21

Severity          : INFORMATION

UTC time          : Fri Nov 23 21:22:05 2007

Mark              : From a Log:: class instance

Brutus server     : xxxxx (replaced by Rob)

Windows domain    : xxxxx (replaced by Rob)

Domain controller : xxxxx (replaced by Rob)

Brutus version    : Brutus Server 0.9.36.1

MAPI version      : Microsoft Exchange 6.5

Process ID        : 544

File              : ..\servant_impl\BrutusLogOnS_impl.cpp

Line              : 261

Following         : #19

Message           : Leaving BRUTUS_BrutusLogOn_i::GetVersion()

---

### Post by jakala on 2007-12-10
Hello,

I have too a problem for use brutus. I think we can help us together. How do you do to have debug message? When I launch evolution via terminal, I just have these lines: 

```
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...

```

---

### Post by ip-rob on 2007-12-10
I've stopped using the brutus-evolution.  Version 2.2 of Evolution is supposed to be using libmapi and have direct MAPI integration.  I think it will be easier to just wait for that version.

---


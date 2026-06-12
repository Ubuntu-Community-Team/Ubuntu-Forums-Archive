---
title: "Start on Stopping (upstart)"
date: 2013-11-28
forum: General Help
---

### Post by m.e.danko on 2013-11-28
Can someone please explain to me how I would go about starting a script before stopping another upstart event?

I have mongodb installed and it's upstart script is located /etc/init/mongodb.conf 

I have made another upstart script called move_docs.conf in /etc/init

with has the following contents 
----------------------------------------------------------------------------------------------------------------------------
start on (stopping mongodb)

script
path_to_script_to_run_here
end script
----------------------------------------------------------------------------------------------------------------------------

Any ideas where I am going wrong? It doesn't seem to want to execute before mongodb shuts down. Any help would be much appreciated.

Many Thanks, Martin.

---


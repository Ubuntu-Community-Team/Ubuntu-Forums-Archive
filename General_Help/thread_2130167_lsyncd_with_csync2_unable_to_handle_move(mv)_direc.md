---
title: "lsyncd with csync2 unable to handle move(mv) directories"
date: 2013-03-28
forum: General Help
---

### Post by prashbs on 2013-03-28
We have an active active nodes and wanted to implement 2 way filesystem replication over WAN.

We  have configured lsyncd with csync2. Everything works fine except when I  execute mv on a subdirectory . Lsyncd is listening on a parent folder.

When  I use mv command to move a nested sub directory to a different location  or within the same folder (for renaming), on the destination server (other active node) it  does create the new directory but unable to remove the orginal  directory. 

lsyncd.conf :

settings = {
        logident        = "lsyncd",
        logfacility    = "user",
        logfile        = "/var/log/lsyncd/lsyncd.log",
        statusFile      = "/var/log/lsyncd/status.log",
        statusInterval  = 1
}

initSync = {
        delay = 1,
        maxProcesses = 10,
        action = function(inlet)
                local config = inlet.getConfig()
                local elist = inlet.getEvents(function(event)
                        return event.etype ~= "Init"
                end)
                local directory = string.sub(config.source, 1, -2)
                local paths = elist.getPaths(function(etype, path)
                        return "\t" .. config.syncid .. ":" .. directory .. path
                end)
                local filelist = elist.getPaths(function(etype, path)
                        return directory .. path
                end)
                log("Normal", "Processing syncing list:\n", table.concat(filelist, "\n"))
              spawn(elist, "/usr/sbin/csync2", "-C", config.syncid, "-x",filelist)
        end,
        collect = function(agent, exitcode)
                local config = agent.config
                if not agent.isList and agent.etype == "Init" then
                        if exitcode == 0 then
                                log("Normal", "Startup of '", config.syncid, "' instance finished.")
                        elseif config.exitcodes and config.exitcodes[exitcode] == "again" then
                                log("Normal", "Retrying startup of '", config.syncid, "' instance.")
                                return "again"
                        else
                                log("Error", "Failure on startup of '", config.syncid, "' instance.")
                                terminate(-1)
                        end
                        return
                end
                local rc = config.exitcodes and config.exitcodes[exitcode]
                if rc == "die" then
                        return rc
                end
                if agent.isList then
                        if rc == "again" then
                                log("Normal", "Retrying events list on exitcode = ", exitcode)
                        else
                                log("Normal", "Finished events list = ", exitcode)
                        end
                else
                        if rc == "again" then
                        log("Normal", "Retrying ", agent.etype, " on ", agent.sourcePath, " = ", exitcode)
                        else
                                log("Normal", "Finished ", agent.etype, " on ", agent.sourcePath, " = ", exitcode)
                        end
                end
                return rc
        end,
        init = function(event)
                local inlet = event.inlet;
                local config = inlet.getConfig()
                log("Normal", "Recursive startup sync: ", config.syncid, ":", config.source)
                spawn(event, "/usr/sbin/csync2", "-C", config.syncid, "-x")
        end,
        prepare = function(config)
                if not config.syncid then
                        error("Missing 'syncid' parameter.", 4)
                end
                local c = "csync2_" .. config.syncid .. ".cfg"
                local f, err = io.open("/etc/csync2/" .. c, "r")
                if not f then
                        error("Invalid 'syncid' parameter: " .. err, 4)
                end
                f:close()
        end
}

local sources = {
        ["/opt/filetest"] = "hcxxx",
        
}
for key, value in pairs(sources) do
        sync {initSync, source=key, syncid=value}
end




Csync2.cfg file conatins

nossl * *;
group hcxxx
{
        host hcxxx;
        host (hcxxx);
        key /etc/csync2/csync2.key;
        include /opt/filetest;
        include /ecx;
        exclude *~ .*;
        auto none;
}

lsyncd is listening on my parent folder /opt/filetest

How  do i handle move (mv or cp)  command so that the original directory is deleted and  then copied, so that the same thing would be replicated on the other  server. Please help.

---


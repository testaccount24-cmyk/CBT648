# CBT648
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. GitHub repos will be deleted and created during this period...

```
//***FILE 648 is from Ben Marino and contains ZRMS, his Resource    *   FILE 648
//*           Monitor Subsystem.  This is a sophisticated and       *   FILE 648
//*           valuable software tool.                               *   FILE 648
//*                                                                 *   FILE 648
//*           email:  Ben Marino <b2marino@outlook.com>             *   FILE 648
//*                                                                 *   FILE 648
//*           Please see the examples at the bottom of member       *   FILE 648
//*           $$DOC.                                                *   FILE 648
//*                                                                 *   FILE 648
//*                            ZRMS                                 *   FILE 648
//*                      RESOURCE MONITOR                           *   FILE 648
//*                          SUBSYSTEM                              *   FILE 648
//*                                                                 *   FILE 648
//*   Resource Monitoring:                                          *   FILE 648
//*     The Resource Monitor Subsystem (ZRMS) allows you to         *   FILE 648
//*     monitor system resource usage. For example, you can use     *   FILE 648
//*     it to monitor common virtual storage usage by specific      *   FILE 648
//*     jobs, started task, and TSO users with minimal overhead.    *   FILE 648
//*     ZRMS gives you the choice of logging monitored data to      *   FILE 648
//*     sequential datasets, PDS members, and/or SMF records.       *   FILE 648
//*     You can use the monitored data to predict problems or       *   FILE 648
//*     constraints before they become critical.                    *   FILE 648
//*                                                                 *   FILE 648
//*   The ZRMS subsystem supports the following monitor facilities: *   FILE 648
//*                                                                 *   FILE 648
//*    - Virtual Storage Monitor Facility                           *   FILE 648
//*    - Authorized Service Monitor Facility                        *   FILE 648
//*    - General Resource Monitor Facility                          *   FILE 648
//*                                                                 *   FILE 648
//*  Virtual Storage Monitor Facility:                              *   FILE 648
//*   The virtual storage monitor facility allows you to monitor    *   FILE 648
//*   the following virtual storage areas:                          *   FILE 648
//*                                                                 *   FILE 648
//*   - E/SQA and E/CSA common virtual storage                      *   FILE 648
//*   - E/LSQA address space virtual storage                        *   FILE 648
//*   - Jobstep task address space virtual storage                  *   FILE 648
//*   - E/PRIVATE address space virtual storage                     *   FILE 648
//*                                                                 *   FILE 648
//*  Authorized Service Monitor Facility:                           *   FILE 648
//*   The authorized service monitor facility allows you to monitor *   FILE 648
//*   authorized system resources. You can use it as follows:       *   FILE 648
//*                                                                 *   FILE 648
//*   - Monitor MODESET authorization service requests              *   FILE 648
//*   - Restrict MODESET authorization service requests             *   FILE 648
//*   - Monitor user-defined service requests                       *   FILE 648
//*   - Restrict user-defined service requests                      *   FILE 648
//*   - Monitor authorized system and subsystem commands            *   FILE 648
//*   - Restrict authorized system and subsystem commands           *   FILE 648
//*                                                                 *   FILE 648
//*  General Resource Monitor Facility:                             *   FILE 648
//*   The general resource monitor facility allows to monitor       *   FILE 648
//*   the following system resources:                               *   FILE 648
//*                                                                 *   FILE 648
//*   - Security server (RACHECK, RACINIT, RACLIST, RACDEF)         *   FILE 648
//*   - Job management (ATTACH, DETACH)                             *   FILE 648
//*   - Program management (LINK, LOAD, DELETE, IDENTIFY, XCTL)     *   FILE 648
//*   - Resource serialization (ENQ, DEQ, RESERVE)                  *   FILE 648
//*   - Real storage management (PGSER, PGFIX, PGFREE, PGOUT)       *   FILE 648
//*   - System resource management (SYSEVENT)                       *   FILE 648
//*   - Dynamic allocation/deallocation (DYNALLOC)                  *   FILE 648
//*   - Data management (OPEN, CLOSE, BLDL, FIND, STOW)             *   FILE 648
//*   - Timer supervision (STIMER, STIMERM)                         *   FILE 648
//*   - I/O management (EXCP, EXCPVR)                               *   FILE 648
//*   - Wait and post management (WAIT, POST, EVENTS)               *   FILE 648
//*                                                                 *   FILE 648
//*  Logging Monitored Resource Data:                               *   FILE 648
//*   You have the option of logging monitored resource data        *   FILE 648
//*   as follows:                                                   *   FILE 648
//*                                                                 *   FILE 648
//*   - Sequential datasets                                         *   FILE 648
//*   - PDS members                                                 *   FILE 648
//*   - SMF                                                         *   FILE 648
//*                                                                 *   FILE 648
//*  ZRMS Subsystem Implementation:                                 *   FILE 648
//*   ZRMS exploits the SUBSYS DD facility of the MVS/SSI to        *   FILE 648
//*   allow you to define system resource monitoring.               *   FILE 648
//*                                                                 *   FILE 648
//*   When you code SUBSYS=ZRMS on DD statements, MVS components,   *   FILE 648
//*   route control, via the SSI, to the ZRMS subsystem. ZRMS       *   FILE 648
//*   takes advantage of the following DD processing phases to      *   FILE 648
//*   create the resource monitoring environment:                   *   FILE 648
//*                                                                 *   FILE 648
//*   - Allocation                                                  *   FILE 648
//*   - Open                                                        *   FILE 648
//*   - Deallocation                                                *   FILE 648
//*   - Close                                                       *   FILE 648
//*                                                                 *   FILE 648
//*  SUBSYS=ZRMS DD Parameters:                                     *   FILE 648
//*   The ZRMS subsystem defines the following resource monitor     *   FILE 648
//*   parameters:                                                   *   FILE 648
//*                                                                 *   FILE 648
//*   SUBSYS=(ZRMS,'DDname,                                         *   FILE 648
//*                 RPT={S|D}                                       *   FILE 648
//*                 SMF={Y|N}                                       *   FILE 648
//*                 SVC={nnn,...|name,...}                          *   FILE 648
//*                 RES={nnn,...|name,...}                          *   FILE 648
//*                 SP={SQA|CSA|LSQA|JST|PVT|ALL|nnn')              *   FILE 648
//*                                                                 *   FILE 648
//*   ZRMS                                                          *   FILE 648
//*    Specifies the ZRMS subsystem name.                           *   FILE 648
//*                                                                 *   FILE 648
//*   DDname                                                        *   FILE 648
//*    Specifies the monitor log DD name. The DD name can point     *   FILE 648
//*    to SYSOUT, sequential, or partitioned dataset member.        *   FILE 648
//*                                                                 *   FILE 648
//*   RPT={D|S}                                                     *   FILE 648
//*    Specifies the monitor report type. "D" logs a detailed       *   FILE 648
//*    report. "S" logs a summary report. If not specified, the     *   FILE 648
//*    default "S".                                                 *   FILE 648
//*                                                                 *   FILE 648
//*   SMF={N|Y}                                                     *   FILE 648
//*    Specifies SMF recording option. "Y" logs monitor report to   *   FILE 648
//*    SMF. If not specified, the default is "N". When "Y" is       *   FILE 648
//*    specified, initialization option SMF=nnn must specify a      *   FILE 648
//*    user-defined SMF record number in the range of 200 to 255.   *   FILE 648
//*    Refer to SRCLIB($OPTIONS) member for implementation          *   FILE 648
//*    details.                                                     *   FILE 648
//*                                                                 *   FILE 648
//*   SVC={nnn|name}                                                *   FILE 648
//*    Specifies which SVCs you wish to monitor. "nnn" allows you   *   FILE 648
//*    to monitor SVCs by number. "name" allows you to monitor      *   FILE 648
//*    SVCs by name. You can combine both SVC numbers and SVC       *   FILE 648
//*    names.                                                       *   FILE 648
//*                                                                 *   FILE 648
//*   DIS={nnn|name}                                                *   FILE 648
//*    Specifies which SVCs you wish to restrict. "nnn" allows      *   FILE 648
//*    you to restrict SVCs by number. "name" allows you to         *   FILE 648
//*    restrict SVCs by name. You can combine both SVC numbers      *   FILE 648
//*    and SVC names.                                               *   FILE 648
//*                                                                 *   FILE 648
//*   SP={nnn,...|nnn:nnn|SQA|CSA|LSQA|PVT|JST|ALL}                 *   FILE 648
//*    Specifies which storage subpools you wish to monitor.        *   FILE 648
//*    Note that the SP= parameter is only valid when specified     *   FILE 648
//*    in conjunction with GETMAIN/FREEMAIN SVCs.                   *   FILE 648
//*                                                                 *   FILE 648
//*    {nnn,...}                                                    *   FILE 648
//*    Allows you to specify the storage subpool by number. If      *   FILE 648
//*    you specify multiple subpools, separate them with commas.    *   FILE 648
//*                                                                 *   FILE 648
//*   SP=SQA                                                        *   FILE 648
//*    Monitors E/SQA subppols 226,239,245,247,248.                 *   FILE 648
//*                                                                 *   FILE 648
//*   SP=CSA                                                        *   FILE 648
//*    Monitors E/CSA subpools 227,228,231,241.                     *   FILE 648
//*                                                                 *   FILE 648
//*   SP=SQA,CSA                                                    *   FILE 648
//*    Monitors E/SQA and E/CSA subpools.                           *   FILE 648
//*                                                                 *   FILE 648
//*   SP=LSQA                                                       *   FILE 648
//*    Monitors E/LSQA subpools 203-205,213-215,223-225,233-235,    *   FILE 648
//*    253-255.                                                     *   FILE 648
//*                                                                 *   FILE 648
//*   SP=JST                                                        *   FILE 648
//*    Monitors jobstep task subpools 129-132,226,244,249.          *   FILE 648
//*                                                                 *   FILE 648
//*   SP=PVT                                                        *   FILE 648
//*    Monitors E/PRIVATE subpools 0-134,229,230,236,237,240-244,   *   FILE 648
//*    249-253.                                                     *   FILE 648
//*                                                                 *   FILE 648
//*   SP=ALL                                                        *   FILE 648
//*    Monitors subpools 0-255.                                     *   FILE 648
//*                                                                 *   FILE 648
```

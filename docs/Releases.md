# Release Notes

### About:
#### Release Cycle:
We track active development through the `develop` branch and verified
stable releases through the `master` branch.  New releases are created and
tagged with the year and month of their release.  When we tag a release,
we update `master` to have the latest stable code.

#### Versioning:
As of 11/06/2017, we are retiring semantic versioning and will instead
use a date based versioning system.  Now, a release version can look
like `17.11` where the "major" number is the year and the "minor" number
is the month.

## v21.10 (10/2020): Bug Fixes, Test cases, Dev Environment Improvements
This release focused on general bug fixing and improving our test/development environments.
A CloudLab template will be available with the latest release here: [https://www.cloudlab.us/p/GWCloudLab/onvm](https://www.cloudlab.us/p/GWCloudLab/onvm)

**New Features and NFs**

- [[243](https://github.com/sdnfv/openNetVM/pull/243)] Adds L3 Switch example based on DPDK `l3fwd` sample code. This NF can forward packets either using longest prefix match or a hash table lookup. 
- [[254](https://github.com/sdnfv/openNetVM/pull/254)] Adds Fair Queue NF that demonstrates how to use advanced rings mode to directly access packets and distribute them to a set of child NFs. Packets are "classified" using a CRC32 hash and assigned to a queue. Queues are then read from in Round Robin order to process packets of different types in a fair way. Contributed by  ([Rohit M P](https://github.com/rohit-mp)) from NITK. 
- [[277](https://github.com/sdnfv/openNetVM/pull/277)] Adds support for Jumbo frame packets. Enable by adding a `-j` flag to the manager's go.sh script.


**Testing and Development Improvements**

- [[296](https://github.com/sdnfv/openNetVM/pull/296)] Adds unit test for NF messaging infrastructure and fixes memory leak related to overflow of message pools [[Issue 293](https://github.com/sdnfv/openNetVM/pull/293)]. 
- [[297](https://github.com/sdnfv/openNetVM/pull/297)] Adds VS Code profile to simplify debugging of NFs. 
- [[302](https://github.com/sdnfv/openNetVM/pull/302)] Adds NF chain performance test to measure and plot inter-NF throughput and latency.
- [[308](https://github.com/sdnfv/openNetVM/pull/308)] Adds socket ID information to NF and manager logging print statements. 

**Miscellaneous Bug and Documentation Fixes**

- [[304](https://github.com/sdnfv/openNetVM/pull/304)] Fixes the NF_TAG of `aes_decrypt` in `openNetVM/examples/aes_decrypt/aesdecrypt.c`.
- [[300](https://github.com/sdnfv/openNetVM/pull/300)] Updates MoonGen installation document to work with the new DPDK version.
- [[270](https://github.com/sdnfv/openNetVM/pull/270)] Fixes issues with relative path in the onvm go script to find the web directory. Now using `$ONVM_HOME` instead of `..`.
- [[272](https://github.com/sdnfv/openNetVM/pull/272)] Fixes two bugs (including Issue #233) where the NF rings would not be cleared after deallocation and an underflow bug in stats.
- [[265](https://github.com/sdnfv/openNetVM/pull/265)] Updates Install README to provide further clarification as well as to include a missing package. 
- [[267](https://github.com/sdnfv/openNetVM/pull/267)] Fixes typos in `onvm_pkt_helper.h`.
- [[317](https://github.com/sdnfv/openNetVM/pull/317)] Fixes the ARP NF endianness for source IP addresses. 
- [[306](https://github.com/sdnfv/openNetVM/pull/306)] Updates linter installation script to use newer versions of cppcheck and Ubuntu.
- [[316](https://github.com/sdnfv/openNetVM/pull/316)] Fixes Speed Tester NF so that it does not crash while loading a PCAP trace with jumbo frames without the correct flags.

Contributors:

- Dennis Afanasev ([dennisafa](https://github.com/dennisafa))
- Noah Chinitz ([NoahChinitzGWU](https://github.com/NoahChinitzGWU))
- Benjamin De Vierno ([bdevierno1](https://github.com/bdevierno1))
- Kevin Deems ([kevindweb](https://github.com/kevindweb))
- Lauren Hahn ([lhahn01](https://github.com/Lhahn01))
- Elliott (Elie) Henne ([elliotthenne](https://github.com/elliotthenne))
- Vivek Jain ([vivek-anand-jain](https://github.com/Vivek-anand-jain))
- Jack Kuo [JackKuo-tw](https://github.com/JackKuo-tw)
- Catherine Meadows ([catherinemeadows](https://github.com/catherinemeadows))
- Rohit M P ([rohit-mp](https://github.com/rohit-mp))
- Leslie Monis [lesliemonis](https://github.com/lesliemonis)
- Peng Wu ([PengWu-wp](https://github.com/PengWu-wp))


## v20.10 (10/2020): OS/Dependency Updates, Bug Fixes, New NFs
A CloudLab template will be available with the latest release here: [https://www.cloudlab.us/p/GWCloudLab/onvm](https://www.cloudlab.us/p/GWCloudLab/onvm)

**Version Updates**

- [[249](https://github.com/sdnfv/openNetVM/pull/249)] Updates ONVM to use DPDK 20.05 and Pktgen 20.05, as well as to run on Ubuntu 20.04 LTS

**Miscellaneous Bug and Documentation Fixes**

- [[216](https://github.com/sdnfv/openNetVM/pull/216)] Related to issues [#200](https://github.com/sdnfv/openNetVM/issues/200) and [#201](https://github.com/sdnfv/openNetVM/issues/201). Removed a few memory leaks. Replaced some libc function calls with the corresponding recommended dpdk function calls. Created new function to free allocated memory upon manager termination. Added if statements to error check after every allocation.
- [[221](https://github.com/sdnfv/openNetVM/pull/221)] Updates Python scripts to use Python 3 rather than Python 2 and adds Python 3 as a dependency in the ONVM Install Guide
- [[224](https://github.com/sdnfv/openNetVM/pull/224)] Use NF data instead of global variables in simple_fwd_tb NF
- [[223](https://github.com/sdnfv/openNetVM/pull/223)] Fixes a bug in the load_generator NF. “Failure to obtain MAC address” error caused the NF to hang, so a function is now called to obtain a fake MAC address in this case.
- [[227](https://github.com/sdnfv/openNetVM/pull/227)] Update stats updating during ONVM_NF_ACTION_OUT action
- [[229](https://github.com/sdnfv/openNetVM/pull/229)] Fixed Issue #[228](https://github.com/sdnfv/openNetVM/issues/228) by properly counting the number of ports in the port mask and comparing it to the number available
- [[235](https://github.com/sdnfv/openNetVM/pull/235)] Changed Pull Request template to remind users to request onto develop instead of master
- [[239](https://github.com/sdnfv/openNetVM/pull/239)] Updates existing Pktgen installation guide by providing clarity on Lua installation and improves ONVM’s Pktgen Wiki page
- [[241](https://github.com/sdnfv/openNetVM/pull/241)] Updated README.md with description of config file
- [[252](https://github.com/sdnfv/openNetVM/pull/252)] Improves ONVM Install Guide to reflect DPDK and Pktgen version updates
- [[258](https://github.com/sdnfv/openNetVM/pull/258)] Updated README.md with description of config file. This relates to PR [241](https://github.com/sdnfv/openNetVM/pull/241), since there are some linter issues with 241, this PR is made to resolve that issue.

**New Features and NFs**

- [[218](https://github.com/sdnfv/openNetVM/pull/218)] Python script that parses a JSON config file to launch multiple NFs
- [[219](https://github.com/sdnfv/openNetVM/pull/219)] Manager has new suggested syntax: `./go.sh -k <port mask> -n <NF core mask> [OPTIONS]`. This replaces the positional argument-based syntax with flags. Also assumes default CPU cores unless the user uses the `-m` flag to specify manager cores
- [[230](https://github.com/sdnfv/openNetVM/pull/230)] Add L2 switch NF. The functionality of this NF is similar to the DPDK l2fwd example

Contributors:

- Dennis Afanasev ([dennisafa](https://github.com/dennisafa))
- Ethan Baron ([EthanBaron14](https://github.com/EthanBaron14))
- Benjamin De Vierno ([bdevierno1](https://github.com/bdevierno1))
- Kevin Deems ([kevindweb](https://github.com/kevindweb))
- Mingyu Ma ([WilliamMaa](https://github.com/WilliamMaa))
- Catherine Meadows ([catherinemeadows](https://github.com/catherinemeadows))
- Sreya Nalla ([sreya](https://github.com/sreyanalla)[nalla](https://github.com/sreyanalla))
- Rohit M P ([rohit-mp](https://github.com/rohit-mp))
- [khaledshahine](https://github.com/khaledshahine)
- Vivek Jain ([vivek-anand-jain](https://github.com/Vivek-anand-jain))

## v20.05 (May 31, 2020): Bug Fixes, Usability Improvements, and Token Bucket NF
A CloudLab template will be available with the latest release here: https://www.cloudlab.us/p/GWCloudLab/onvm

### Miscellaneous Bug and Documentation Fixes

- [[158](https://github.com/sdnfv/openNetVM/pull/158)] Print a warning message when the user specifies a specific core (`-l`) for NF to start on but doesn't specify a `-m` flag to use that core for NF to run on. To force an NF to run on a specific core, the `-m` flag must be used, otherwise the Manager will assign the NF to a free core.
- [[159](https://github.com/sdnfv/openNetVM/pull/159)] In `onvm_ft_create` instead of calling `rte_hash_create` from secondary process (NF), enqueue a message for the primary process (onvm_mgr) to do it and then return a pointer.
- [[160](https://github.com/sdnfv/openNetVM/pull/160)] Fixes the case when packets that had an invalid out port would crash the manager. This is done by maintaining a port init array.
- [[166](https://github.com/sdnfv/openNetVM/pull/180), [209](https://github.com/sdnfv/openNetVM/pull/209/files)] Updates dependencies mentioned in [194](https://github.com/sdnfv/openNetVM/pull/194) by updating Acorn’s version from 5.7.3 to 5.7.4 for ONVM Web
- [[173](https://github.com/sdnfv/openNetVM/pull/173)] Fixes a bug in load_generator that caused a seg fault, the NF wasn't calling the setup function before running.
- [[180](https://github.com/sdnfv/openNetVM/pull/180)] Prevent user from running multiple managers or starting an NF prior to the manager.
- [[183](https://github.com/sdnfv/openNetVM/pull/183)] Improved style and efficiency of bash shell scripts using ShellCheck linter
- [[189](https://github.com/sdnfv/openNetVM/pull/189)] Fixes broken links in Moongen and Pktgen installation guides
- [[197](https://github.com/sdnfv/openNetVM/pull/197)] Fixes error where manager cannot start because base address for shared memory region is already in use which would cause `Cannot mmap memory for rte_config` error.
- [[202](https://github.com/sdnfv/openNetVM/pull/202)] Allows Dockers to run on Ubuntu 18.04 successfully. Bug fixes allow NFs to be run both within or outside a container where checks for a running manager and manager duplication are only done when an NF is running outside a container.
- [[204](https://github.com/sdnfv/openNetVM/pull/204)] UDP source port and destination port packet headers are now converted from Big Endian to CPU order, using built-in DPDK conversion method, resulting in correct packet information printing.

###  New Features and NFs

- [[178](https://github.com/sdnfv/openNetVM/pull/178)] Dynamically allocates memory for NF data structures when NFs start instead of statically at program initialization. Maximum number of NFs is still limited `MAX_NFS` in `onvm_common.h` (default is 128).
- [[179](https://github.com/sdnfv/openNetVM/pull/179)] NFs print summary statistics when exiting
- [[196](https://github.com/sdnfv/openNetVM/pull/196)] Continuous Integration improvements
    - Created a Github Action to run linter on incoming PRs. Also checks if the PR was submitted to the `develop` branch.
    - Added three static analysis tools.
        - Pylint
        - Cppcheck
        - Shellcheck
    - New scripts for researchers to install necessary dependencies and run linter locally.
    - Removed CI code from the main repository
- [[199](https://github.com/sdnfv/openNetVM/pull/199)] Added new Simple Forward Token Bucket Rate Limiter NF that simulates a queue with a token bucket and forwards packets to a specific destination.  The NF forwards packets based on a user specified rate (-R) and depth (-D).

Contributors:

- Dennis Afanasev ([dennisafa](https://github.com/dennisafa))
- Ethan Baron ([EthanBaron14](https://github.com/EthanBaron14))
- Benjamin De Vierno ([bdevierno1](https://github.com/bdevierno1))
- Kevin Deems ([kevindweb](https://github.com/kevindweb))
- Mingyu Ma ([WilliamMaa](https://github.com/WilliamMaa))
- Catherine Meadows ([catherinemeadows](https://github.com/catherinemeadows))
- Sreya Nalla ([sreya519](https://github.com/sreya519))
- Rohit M P ([rohit-mp](https://github.com/rohit-mp))


## v19.07 (7/19): NFD library and example NFs, Continuous Integration updates, minor improvements and bug fixes.
A CloudLab template is available with the latest release here: https://www.cloudlab.us/p/GWCloudLab/onvm

**Performance**: This release includes a new macro `ENABLE_FLOW_LOOKUP` which controls whether a flow lookup is performed for every incoming packet. If disabled, all packets are forwarded to the default service ID which improves performance. The flow lookup is still enabled by default for backward compatibility with other applications that use ONVM.

### NFD library with example NFS
Add example NFs based on NFD, a C++-based NF developing compiler designed by Wenfei Wu's group (http://wenfei-wu.github.io/) from IIIS, Tsinghua University, China. NFD compiles the NF logic into a common C++ program by using table-form language to model NFs' behavior.

**The NFD compiler itself isn't included, only the NFs that were created with it.**

A list of provided NFs using NFD library:
 - DNS Amplification Mitigation
 - Super Spread Detection
 - Heavy Hitter Detection
 - SYN Flood Detection
 - UDP Flood Detection
 - Stateless Firewall
 - Stateful Firewall
 - NAPT

### Continuous Integration updates:
CI got a few major updates this release:
 - CI will do basic lint checks and branch checks(all PRs should be submitted against the *develop* branch) for unauthorized users
 - If CI is working on a request and receives another request it will append it to the queue instead of dropping it
 - CI will now run Pktgen as an additional test metric.

### Minor improvements
**Shared core functionality for messages** - adds functionality for NFs using shared core mode to work with NF messages. This means the NF will now sleep when no messages and no packets are enqueued onto a NF's message ring and wakeup if either one is received.  

**NF core rebalancing** - adds functionality for onvm_mgr to remap a NF to a different core, if such occurs(when another NF shuts down). This is disabled by default and can be enabled using the `ONVM_NF_SHUTDOWN_CORE_REASSIGNMENT` macro.

### Bug fixes:
 - Fix Style guide links
 - Fix Typo in Stats Header bug fix
 - Fix Stats Header in Release Notes (twice)

## v19.05 (5/19): Shared Core Mode, Major Architectural Changes, Advanced Rings Changes, Stats Updates, CI PR Review, LPM Firewall NF, Payload Search NF, TTL Flags, minor improvements and bug fixes.
A CloudLab template is available with the latest release here: https://www.cloudlab.us/p/GWCloudLab/onvm

**This release features a lot of breaking API changes.**

**Performance**: This release increases Pktgen benchmark performance from 7Mpps to 13.1 Mpps (measured by Pktgen sending packets to the ONVM Basic Monitor), thus fixing the major performance issue that was present in the last release.

**Repo changes**: Default branch has been changed to `master`, active development can still be seen in `develop`. Most of the development is now done on the public repo to improve visibility, planned projects and improvements can be seen in this [pinned issue](https://github.com/sdnfv/openNetVM/issues/91), additionally pull requests and issues are now cataloged by tags. We're also starting to merge releases into master by pull requests, thus developers should branch off the develop branch and submit PRs against the develop branch.

**Note**: If the NFs crash with this error - `Cannot mmap memory for rte_config at [0x7ffff7ff3000], got [0x7ffff7ff2000]`, simply use the `-a 0x7f000000000` flag for the onvm_mgr, this will resolve the issue.

### Shared Core Mode:
This code introduces **EXPERIMENTAL** support to allow NFs to efficiently run on **shared** CPU cores. NFs wait on semaphores when idle and are signaled by the manager when new packets arrive. Once the NF is in wake state, no additional notifications will be sent until it goes back to sleep. Shared core variables for mgr are in the `nf_wakeup_info` structs, the NF shared core vars were moved to the `onvm_nf` struct.

The code is based on the hybrid-polling model proposed in [_Flurries: Countless Fine-Grained NFs for Flexible Per-Flow Customization_ by Wei Zhang, Jinho Hwang, Shriram Rajagopalan, K. K. Ramakrishnan, and Timothy Wood, published at _Co-NEXT 16_][flurries_paper] and extended in [_NFVnice: Dynamic Backpressure and Scheduling for NFV Service Chains_ by Sameer G. Kulkarni, Wei Zhang, Jinho Hwang, Shriram Rajagopalan, K. K. Ramakrishnan, Timothy Wood, Mayutan Arumaithurai and Xiaoming Fu, published at _SIGCOMM '17_][nfvnice_paper]. Note that this code does not contain the full Flurries or NFVnice systems, only the basic support for shared-Core NFs. However, we have recently released a full version of the NFVNice system as an experimental branch, which can be found [here][nfvnice_branch].

Usage and implementation details can be found [here][shared_core_docs].

### Major Architectural Changes:
- Introduce a local `onvm_nf_init_ctx` struct allocated from the heap before starting onvm.

    Previously the initialization sequence for NFs wasn't able to properly cleanup if a signal was received. Because of this we have introduced a new NF context struct(`onvm_nf_local_ctx`) which would be malloced before initialization begins and would help handle cleanup. This struct contains relevant information about the status of the initialization sequence and holds a reference to the `onvm_nf` struct which has all the information about the NF.  

- Reworking the `onvm_nf` struct.

    Previously the `onvm_nf` struct contained a pointer to the `onvm_nf_info`, which was used during processing. It's better to have one main struct that represents the NF, thus the contents of the `onvm_nf_info` were merged into the `onvm_nf` struct. This allows us to maintain a cleaner API where all information about the NF is stored in the `onvm_nf` struct.  

 - Replace the old `onvm_nf_info` with a new `onvm_nf_init_ctx` struct that is passed to onvm_mgr for initialization.

    This struct contains all relevant information to spawn a new NF (service/instance IDs, flags, core, etc). When the NF is spawned this struct will be released back to the mempool.  


 - Adding a function table struct `onvm_nf_function_table`.  

    Finally, we introduced the `onvm_nf_function_table` struct that groups all NF callback functions that can be set by developers.   

**Overall, the new NF launch/shutdown sequence looks as follows:**
```c
struct onvm_nf_local_ctx *nf_local_ctx;        
struct onvm_nf_function_table *nf_function_table;

nf_local_ctx = onvm_nflib_init_nf_local_ctx();
onvm_nflib_start_signal_handler(nf_local_ctx, NULL);

nf_function_table = onvm_nflib_init_nf_function_table();
nf_function_table->pkt_handler = &packet_handler;

if ((arg_offset = onvm_nflib_init(argc, argv, NF_TAG, nf_local_ctx, nf_function_table)) < 0)
        // error checks

argc -= arg_offset;
argv += arg_offset;

if (parse_app_args(argc, argv, progname) < 0)
        // error checks

onvm_nflib_run(nf_local_ctx);
onvm_nflib_stop(nf_local_ctx);
```  

### Advanced Rings Changes:
This release changes our approach to NFs using the advanced rings mode. Previously we were trying to provide APIs for advanced ring developers such as scaling, but this logic should be managed by the NFs themselves. Because of this we're reworking those APIs and letting the NF devs handle everything themselves.  
 - Speed Tester NF advanced rings mode is removed
 - Extra APIs have been removed
 - Removes support for advanced rings scaling APIs
 - Scaling Example NF advanced rings mode has been reworked, the new implementation now does its own pthread creation instead of relying on the onvm scaling APIs. Also makes a clear separation between default and advanced ring mode.  
 - Because of these changes some internal nflib APIs were exposed to the NF (`onvm_nflib_start_nf`, `onvm_nflib_init_nf_init_cfg`, `onvm_nflib_inherit_parent_init_cfg`)

### Stats Updates:
This release updates both console and web stats.

 - For web stats this adds the Core Mappings page with the core layout for both onvm_mgr and NFs.
 - For console stats this overhauls the displayed stats and adds new information, see more below.

The new default mode now displays NF tag and core ID:
```
PORTS
-----
Port 0: '90:e2:ba:b3:bc:6c'

Port 0 - rx:         4  (        0 pps) tx:         0  (        0 pps)

NF TAG         IID / SID / CORE    rx_pps  /  tx_pps        rx_drop  /  tx_drop           out   /    tonf     /   drop
----------------------------------------------------------------------------------------------------------------------
speed_tester    1  /  1  /  4      1693920 / 1693920               0 / 0                      0 / 40346970    / 0
```

Verbose mode also adds `PNT`(Parent ID), `S|W`(NF state, sleeping or working), `CHLD`(Children count):
```
PORTS
-----
Port 0: '90:e2:ba:b3:bc:6c'

Port 0 - rx:         4  (        0 pps) tx:         0  (        0 pps)

NF TAG         IID / SID / CORE    rx_pps  /  tx_pps             rx  /  tx                out   /    tonf     /   drop
               PNT / S|W / CHLD  drop_pps  /  drop_pps      rx_drop  /  tx_drop           next  /    buf      /   ret
----------------------------------------------------------------------------------------------------------------------
speed_tester    1  /  1  /  4      9661664 / 9661664        94494528 / 94494528               0 / 94494487    / 0
                0  /  W  /  0            0 / 0                     0 / 0                      0 / 0           / 128
```

The shared core mode adds wakeup information stats:
```
PORTS
-----
Port 0: '90:e2:ba:b3:bc:6c'

Port 0 - rx:         5  (        0 pps) tx:         0  (        0 pps)

NF TAG         IID / SID / CORE    rx_pps  /  tx_pps             rx  /  tx                out   /    tonf     /   drop
               PNT / S|W / CHLD  drop_pps  /  drop_pps      rx_drop  /  tx_drop           next  /    buf      /   ret
                                  wakeups  /  wakeup_rt
----------------------------------------------------------------------------------------------------------------------
simple_forward  2  /  2  /  4        27719 / 27719            764439 / 764439                 0 / 764439      / 0
                0  /  S  /  0            0 / 0                     0 / 0                      0 / 0           / 0
                                    730557 / 25344

speed_tester    3  /  1  /  5        27719 / 27719            764440 / 764439                 0 / 764440      / 0
                0  /  W  /  0            0 / 0                     0 / 0                      0 / 0           / 1
                                    730560 / 25347



Shared core stats
-----------------
Total wakeups = 1461122, Wakeup rate = 50696
```

The super verbose stats mode has also been updated to include new stats:
```
#YYYY-MM-DD HH:MM:SS,nic_rx_pkts,nic_rx_pps,nic_tx_pkts,nic_tx_pps
#YYYY-MM-DD HH:MM:SS,nf_tag,instance_id,service_id,core,parent,state,children_cnt,rx,tx,rx_pps,tx_pps,rx_drop,tx_drop,rx_drop_rate,tx_drop_rate,act_out,act_tonf,act_drop,act_next,act_buffer,act_returned,num_wakeups,wakeup_rate
2019-06-04 08:54:52,0,4,4,0,0
2019-06-04 08:54:53,0,4,0,0,0
2019-06-04 08:54:54,simple_forward,1,2,4,0,W,0,29058,29058,29058,29058,0,0,0,0,0,29058,0,0,0,0,28951,28951
2019-06-04 08:54:54,speed_tester,2,1,5,0,S,0,29058,29058,29058,29058,0,0,0,0,0,29059,0,0,0,1,28952,28952
2019-06-04 08:54:55,0,4,0,0,0
2019-06-04 08:54:55,simple_forward,1,2,4,0,W,0,101844,101843,72785,72785,0,0,0,0,0,101843,0,0,0,0,101660,101660
2019-06-04 08:54:55,speed_tester,2,1,5,0,W,0,101844,101843,72785,72785,0,0,0,0,0,101844,0,0,0,1,101660,101660
```

### CI PR Review:
CI is now available on the public branch. Only a specific list of whitelisted users can currently run CI for security purposes. The new CI system is able to approve/reject pull requests.
CI currently performs these checks:
 - Check the branch (for our discussed change of develop->master as main branch)
 - Run performance check (speed tester currently with 35mil benchmark)
 - Run linter (only on the PR diff)

### LPM Firewall NF:
The firewall NF drops or forwards packets based on rules provided in a JSON config file. This is achieved using DPDK's LPM (longest prefix matching) library. Default behavior is to drop a packet unless the packet matches a rule. The NF also has a debug mode to print decisions for every packet and an inverse match mode where default behavior is to forward a packet if it is not found in the table. Documentation for this NF can be found [here][firewall_nf_readme].

### Payload Search NF:
The Payload Scan NF provides the functionality to search for a string within a given UDP or TCP packet payload. Packet is forwarded to its destination NF on a match, dropped otherwise. The NF also has an inverse mode to drop on match and forward otherwise. Documentation for this NF can be found [here][payload_scan_nf_readme].

### TTL Flags:
Adds TTL and packet limit flags to stop the NF or the onvm_mgr based on time since startup or based on packets received. Default measurements for these flags are in seconds and in millions of packets received.

### NF to NF Messaging:
Adds the ability for NFs to send messages to other NFs. NFs need to define a message handler to receive messages and are responsible to free the custom message data. If the message is sent to a NF that doesn't have a message handler the message is ignored.

### Minor improvements
 - **Make Number of mbufs a Constant Value** - Previously the number of mbufs was calculated based on the `MAX_NFS` constant. This led to performance degradation as the requested number of mbufs was too high, changing this to a constant has significantly improved performance.  
 - **Reuse NF Instance IDs** - Reuse instance IDs of old NFs that have terminated. The instance IDs are still continiously incremented up to the `MAX_NFS` constant, but when that number is reached the next NF instance ID will be wrapped back to the starting value and find the first unoccupied instance ID.   
 - Fix all major style errors
 - Check if ONVM_HOME is Set Before Compiling ONVM   
 - Add Core Information to Web Stats
 - Update Install Script Hugepage Setup & Kernel Driver Installation  
 - Add Compatibility Changes to Run ONVM on Ubuntu 18.04.1  
 - Various Documentation updates and fixes  
 - Change onvm-pktgen Submodule to Upstream Pktgen  

### Bug fixes:
 - Free Memory on ONVM_MGR Shutdown  
 - Launch Script to Handle Multi-word String Arguments  
 - NF Advanced Ring Thread Process NF Shutdown Messages  
 - Adds NF Ring Cleanup Logic On Shutdown  
 - Resolve Shutdown Memory Leaks  
 - Add NF Tag Memory Allocation  
 - Fix the Parse IP Helper Function  
 - Fix Speed Tester NF Generated Packets Counter  
 - Add Termination of Started but not yet Running NFs  
 - Add ONVM mgr web mode memory cleanup on shutdown  
 - Removes the Old Flow Tracker NF Launch Script  
 - Fix Deprecated DPDK Function in Speed Tester NF  

**v19.05 API Struct changes:**

* Adding `onvm_nf_local_ctx` which is malloced and passed into `onvm_nflib_init`:
    ```c
    struct onvm_nf_local_ctx {
            struct onvm_nf *nf;
            rte_atomic16_t nf_init_finished;
            rte_atomic16_t keep_running;
    };
    ```

* Adding a function table for eaiser callback managing:
    ```c
    struct onvm_nf_function_table {
            nf_setup_fn  setup;
            nf_msg_handler_fn  msg_handler;
            nf_user_actions_fn user_actions;
            nf_pkt_handler_fn  pkt_handler;
    };
    ```

* Renaming the old `onvm_nf_info` -> `onvm_nf_init_cfg`:
    ```c
    struct onvm_nf_init_cfg {
            uint16_t instance_id;
            uint16_t service_id;
            uint16_t core;
            uint16_t init_options;
            uint8_t status;
            char *tag;
            /* If set NF will stop after time reaches time_to_live */
            uint16_t time_to_live;
            /* If set NF will stop after pkts TX reach pkt_limit */
            uint16_t pkt_limit;
    };
    ```

* Consolidating previous `onvm_nf_info` and `onvm_nf` into a singular `onvm_nf` struct:  
    ```c
    struct onvm_nf {
            struct rte_ring *rx_q;
            struct rte_ring *tx_q;
            struct rte_ring *msg_q;
            /* Struct for NF to NF communication (NF tx) */
            struct queue_mgr *nf_tx_mgr;
            uint16_t instance_id;
            uint16_t service_id;
            uint8_t status;
            char *tag;
            /* Pointer to NF defined state data */
            void *data;

            struct {
                    uint16_t core;
                    /* Instance ID of parent NF or 0 */
                    uint16_t parent;
                    rte_atomic16_t children_cnt;
            } thread_info;

            struct {
                    uint16_t init_options;
                    /* If set NF will stop after time reaches time_to_live */
                    uint16_t time_to_live;
                    /* If set NF will stop after pkts TX reach pkt_limit */
                    uint16_t pkt_limit;
            } flags;

            /* NF specific functions */
            struct onvm_nf_function_table *function_table;

            /*
             * Define a structure with stats from the NFs.
             *
             * These stats hold how many packets the NF will actually receive, send,
             * and how many packets were dropped because the NF's queue was full.
             * The port-info stats, in contrast, record how many packets were received
             * or transmitted on an actual NIC port.
             */
            struct {
                    volatile uint64_t rx;
                    volatile uint64_t rx_drop;
                    volatile uint64_t tx;
                    volatile uint64_t tx_drop;
                    volatile uint64_t tx_buffer;
                    volatile uint64_t tx_returned;
                    volatile uint64_t act_out;
                    volatile uint64_t act_tonf;
                    volatile uint64_t act_drop;
                    volatile uint64_t act_next;
                    volatile uint64_t act_buffer;
            } stats;

            struct {
                     /*
                      * Sleep state (shared mem variable) to track state of NF and trigger wakeups
                      *     sleep_state = 1 => NF sleeping (waiting on semaphore)
                      *     sleep_state = 0 => NF running (not waiting on semaphore)
                      */
                    rte_atomic16_t *sleep_state;
                    /* Mutex for NF sem_wait */
                    sem_t *nf_mutex;
            } shared_core;
    };
    ```

**v19.05 API Changes:**
 - `int onvm_nflib_init(int argc, char *argv[], const char *nf_tag, struct onvm_nf_info **nf_info_p)` -> `int onvm_nflib_init(int argc, char *argv[], const char *nf_tag, struct onvm_nf_local_ctx *nf_local_ctx, struct onvm_nf_function_table *nf_function_table)`
 - `int onvm_nflib_run(struct onvm_nf_info* info, pkt_handler_func pkt_handler)` -> `int onvm_nflib_run(struct onvm_nf_local_ctx *nf_local_ctx)`
 - `int onvm_nflib_return_pkt(struct onvm_nf_info *nf_info, struct rte_mbuf* pkt)` -> `int onvm_nflib_return_pkt(struct onvm_nf *nf, struct rte_mbuf *pkt)`
 - `int onvm_nflib_return_pkt_bulk(struct onvm_nf_info *nf_info, struct rte_mbuf** pkts, uint16_t count)` -> `onvm_nflib_return_pkt_bulk(struct onvm_nf *nf, struct rte_mbuf **pkts, uint16_t count)`
 - `int onvm_nflib_nf_ready(struct onvm_nf_info *info)` -> `int onvm_nflib_nf_ready(struct onvm_nf *nf)`
 - `int onvm_nflib_handle_msg(struct onvm_nf_msg *msg, __attribute__((unused)) struct onvm_nf_info *nf_info)` ->
 `int onvm_nflib_handle_msg(struct onvm_nf_msg *msg, struct onvm_nf_local_ctx *nf_local_ctx)`
 - `void onvm_nflib_stop(struct onvm_nf_info *nf_info)` -> `void onvm_nflib_stop(struct onvm_nf_local_ctx *nf_local_ctx)`
 - `struct onvm_nf_scale_info *onvm_nflib_get_empty_scaling_config(struct onvm_nf_info *parent_info)` ->   `struct onvm_nf_scale_info *onvm_nflib_get_empty_scaling_config(struct onvm_nf *nf)`
 - `struct onvm_nf_scale_info *onvm_nflib_inherit_parent_config(struct onvm_nf_info *parent_info, void *data)` ->
`struct onvm_nf_scale_info *onvm_nflib_inherit_parent_config(struct onvm_nf *nf, void *data)`

**v19.05 API Additions:**
 - `struct onvm_nf_local_ctx *onvm_nflib_init_nf_local_ctx(void)`
 - `struct onvm_nf_function_table *onvm_nflib_init_nf_function_table(void)`
 - `int onvm_nflib_start_signal_handler(struct onvm_nf_local_ctx *nf_local_ctx, handle_signal_func signal_hanlder)`
 - `int onvm_nflib_send_msg_to_nf(uint16_t dest_nf, void *msg_data)`
 - `int onvm_nflib_request_lpm(struct lpm_request *req)`
 - `struct onvm_configuration *onvm_nflib_get_onvm_config(void)`  
    These APIs were previously internal but are now exposed for advanced ring NFs:
 - `int onvm_nflib_start_nf(struct onvm_nf_local_ctx *nf_local_ctx, struct onvm_nf_init_cfg *nf_init_cfg)`
 - `struct onvm_nf_init_cfg *onvm_nflib_init_nf_init_cfg(const char *tag)`
 - `struct onvm_nf_init_cfg *onvm_nflib_inherit_parent_init_cfg(struct onvm_nf *parent)`

**v19.05 Removed APIs:**
 - `int onvm_nflib_run_callback(struct onvm_nf_info* info, pkt_handler_func pkt_handler, callback_handler_func callback_handler)`
 - `struct rte_ring *onvm_nflib_get_tx_ring(struct onvm_nf_info* info)`
 - `struct rte_ring *onvm_nflib_get_rx_ring(struct onvm_nf_info* info)`
 - `struct onvm_nf *onvm_nflib_get_nf(uint16_t id)`
 - `void onvm_nflib_set_setup_function(struct onvm_nf_info* info, setup_func setup)`

## v19.02 (2/19): Manager Assigned NF Cores, Global Launch Script, DPDK 18.11 Update, Web Stats Overhaul, Load Generator NF, CI (Internal repo only), minor improvements and bug fixes
This release adds several new features and changes how the onvm_mgr and NFs start. A CloudLab template is available with the latest release here: https://www.cloudlab.us/p/GWCloudLab/onvm

Note: This release makes important changes in how NFs are run and assigned to cores.

Performance: We are aware of some performance irregularities with this release. For example, the first few times a Basic Monitor NF is run we achieve only ~8 Mpps on a CloudLab Wisconsin c220g2 server. After starting and stopping the NF several times, the performance rises to the expected 14.5 Mpps.

### Manager Assigned NF Cores:
NFs no longer require a CORE_LIST argument to start, the manager now does core assignment based on the provided core bitmask argument.

NFs now go through the dpdk init process on a default core (currently 0) and then launch a pthread for its main loop, which using the DPDK `rte_thread_set_affinity()` function is affinized to a core obtained from the Manager.

The core info is maintained in a memzone and the Manager keeps track of what cores are used, by how many NFs, and if the cores are reserved as dedicated. The Manager always selects the core with the fewest NFs unless a flag is used when starting an NF.

**Usage:**

New Manager arguments:
  * Hexadecimal bitmask, which tells the onvm_mgr which cores are available for NFs to run on.

The manager now must be run with a command like:
```sh
cd onvm
#./go.sh CORE_LIST PORT_BITMASK NF_CORE_BITMASK -s LOG_MODE
./go.sh 0,1,2,3 0x3 0xF0 -s stdout

```
With this command the manager runs on cores 0-3, uses ports 1 and 2 (since `0x3` is binary `0b11`), and will start NFs on cores 4-7 (since `0xF0` is binary `0b11110000`)

New Network Functions arguments:
  * `-m` manual core decision mode, NF runs on the core supplied by the `-l` argument if available. If the core is busy or not enabled then returns an error and doesn't start the NF.
  * `-s` shared core mode, this will allow multiple NFs to run on the same core. Generally this should be avoided to prevent performance problems. By default, each core is dedicated to a single NF.

These arguments can be set as `ONVM_ARGS` as detailed below.

**API Additions:**
 - `int onvm_threading_core_affinitize(int core)` - Affinitizes the calling thread to a new core. This is used both internally and by the advanced rings NFs to change execution cores.  

### Global Launch Script
The example NFs can be started using the `start_nf.sh` script. The script can run any example NF based on the first argument which is the NF name (this is based on the assumption that the name matches the NF folder and the build binary). This removes the need to maintain a separate `go.sh` script for each NF but requires some arguments to be explicitly specified.

The script has 2 modes:
 - Simple
    ```sh
    ./start_nf.sh NF_NAME SERVICE_ID (NF_ARGS)
    ./start_nf.sh speed_tester 1 -d 1
    ```
  - Complex
    ```sh
    ./start_nf.sh NF_NAME DPDK_ARGS -- ONVM_ARGS -- NF_ARGS
    ./start_nf.sh speed_tester -l 4 -- -s -r 6 -- -d 5
    ```
*All the NF directories have a symlink to `examples/go.sh` file which allows to omit the NF name argument when running the NF from its directory:*
```sh
    cd speed_tester && ./go.sh 1 -d 1
    cd speed_tester && ./go.sh -l 4 -- -s -r 6 -- -d 5
```


### DPDK 18.11 Update
DPDK submodule no longer points to our fork, we now point to the upstream DPDK repository. This is because mTCP requirements for DPDK have relaxed and they no longer need to have additional patches on top of it.  

Also updates Pktgen to 3.6.5 to remain compatible with DPDK v18.11
The dpdk update involves:
- Adds NIC ring RSS hashing functions adjustments
- Adds NIC ring file descriptor size alignment

Run this to ensure the submodule is up to date:
```sh
git submodule sync
git submodule update --init
```

### Web Stats Overhaul
Adds a new event logging system which is used for port initialization and NF starting, ready, and stopping events. In the future, this could be used for more complex logging such as service chain based events and for core mappings.

Also contains a complete rewrite of the web frontend. The existing code which primarily used jquery has been rewritten and expanded upon in React, using Flow for type checking rather than a full TypeScript implementation. This allows us to maintain application state across pages and to restore graphs to the fully updated state when returning to a graph from a different page.

Please note that **CSV download has been removed** with this update as storing this much ongoing data negatively impacts application performance. This sort of data collection would be best implemented via grepping or some similar functionality from onvm console output.

### Load Generator NF
Adds a Load Generator NF, which sends packets at a specified rate and size, measures tx and rx throughput (pps) and latency. The load_generator NF continuously allocates and sends new packets of a defined size and at a defined rate using the `callback_handler` function. The max value for the `-t` pkt_rate argument for this NF will depend on the underlying architecture, for best performance increase it up until you see the NF starting to drop packets.

Example usage with a chain of load_generator <-> simple_forward:
```sh
cd examples/load_generator
./go.sh 1 -d 2 -t 4000000

cd examples/simple_forward
./go.sh 2 -d 1
```

Example NF output:
```
Time elapsed: 24.50

Tx total packets: 98001437
Tx packets sent this iteration: 11
Tx rate (set): 4000000
Tx rate (average): 3999999.33
Tx rate (current): 3999951.01

Rx total packets: 94412314
Rx rate (average): 3853506.69
Rx rate (current): 4000021.01
Latency (current mean): 4.38 us
```


### CI (Internal repo only)
Adds continuous integration to the internal repo. CI will automatically run when a new PR is created or when keyword `@onvm` is mentioned in a pr comment. CI currently reports the linter output and the Speed Tester NF performance. This will be tested internally and extended to support the public repo when ready.  

To achieve this a Flask server listens to events from github, currently only the `openNetVM-dev` repo is setup for this. In the future we plan to expand this functionality to the public `openNetVM` repo.  

### Bug Fixes
 - Fix how NF_STOPPED message is sent/processed. This fixes the double shutdown bug (observed in mTCP applications), the fast ctrl-c exit bug and the invalid arguments bug. In all of those cases memory would get corrupted, this bug fix resolves these cases.  
 - Add out of bounds checks for NF service ids. Before we were not handling cases when a new NF service id exceeded the MAX_SERVICES value or when launching a new NF would exceed the NF_SERVICE_COUNT_MAX value for the given service id.  
 - Fix the Speed Tester NF to properly exit when passed an invalid MAC addr argument.  

## v18.11 (11/18): Config files, Multithreading, Better Statistics, and bug fixes
This release adds several new features which cause breaking API changes to existing NFs.  NFs must be updated to support the new API required for multithreading support. A CloudLab template is available with the latest release here: https://www.cloudlab.us/p/GWCloudLab/onvm

 ### Multithreading:
NFs can now run multiple threads, each with its own set of rings for receiving and transmitting packets. NFs can either start new threads themselves or the NF Manager can send a message to an NF to cause it to scale up.

**Usage:**
To make an NF start another thread, run the `onvm_nflib_scale(struct onvm_nf_scale_info *scale_info)` function with a struct holding all the information required to start the new NF thread. This can be used to replicate an NF's threads for scalability (all with same service ID), or to support NFs that require several threads performing different types of processing (thus each thread has its own service ID). More info about the multithreading can be found in `docs/NF_Dev.md`. Example use of multithreading NF scaling can be seen in the `scaling_example` NF.

**API Changes:**
The prior code relied on global data structures that do not work in a multithreaded environment. As a result, many of the APIs have been refactored to take an `onvm_nf_info` structure, instead of assuming it is available as a global variable.
 - `int onvm_nflib_init(int argc, char *argv[], const char *nf_tag);` ->
`int onvm_nflib_init(int argc, char *argv[], const char *nf_tag, struct onvm_nf_info **nf_info_p)`
 - `void onvm_nflib_stop(void)` -> `void onvm_nflib_stop(struct onvm_nf_info *nf_info)`
- `int onvm_nflib_return_pkt(struct rte_mbuf* pkt)` ->
`int onvm_nflib_return_pkt(struct onvm_nf_info *nf_info, struct rte_mbuf* pkt)`
- `int pkt_handler_func(struct rte_mbuf* pkt, struct onvm_pkt_meta* action)` ->
`int pkt_handler_func(struct rte_mbuf *pkt, struct onvm_pkt_meta *meta, __attribute__ ((unused)) struct onvm_nf_info *nf_info)`
- `int callback_handler_func(void)` -> `int callback_handler_func(__attribute__ ((unused)) struct onvm_nf_info *nf_info)`
- Any existing NFs will need to be modified to support this updated API. Generally this just requires adding a reference to the `onvm_nf_info` struct in the API calls.

NFs also must adjust their Makefiles to include the following libraries:
```
CFLAGS += -I$(ONVM)/lib
LDFLAGS += $(ONVM)/lib/$(RTE_TARGET)/lib/libonvmhelper.a -lm
```

**API Additions:**
 - `int onvm_nflib_scale(struct onvm_nf_scale_info *scale_info)` launches another NF based on the provided config
 - `struct onvm_nf_scale_info * onvm_nflib_get_empty_scaling_config(struct onvm_nf_info *parent_info)` for getting a basic empty scaling config
 - `struct onvm_nf_scale_info * onvm_nflib_inherit_parent_config(struct onvm_nf_info *parent_info)` for getting a scaling config with the same functionality (e.g., service ID) as the parent NF
 - `void onvm_nflib_set_setup_function(struct onvm_nf_info* info, setup_func setup)` sets the setup function to be automatically executed once before an NF enters the main packet loop  

### Stats Display  
The console stats display has been improved to aggregate stats when running multiple NFs with the same service ID and to add two additional modes: verbose for all stats in human readable format and raw stats dump for easy script parsing. The NF TX stat has been updated to also include tonf traffic.


**Usage:**   
- For normal mode no extra steps are required  
- For verbose mode run the manager with `-v` flag  
- For raw stats dump use the `-vv` flag  

### Config File Support:
ONVM now supports JSON config files, which can be loaded through the API provided in `onvm_config_common.h`. This allows various settings of either the ONVM manager or NFs to be set in a JSON config file and loaded into code, as opposed to needing to be passed in via the command line.

**Usage:**
 - All example NFs now support passing DPDK and ONVM arguments in a config file by using the `-F config.json` flag when running an NF executable or a `go.sh` script.  See `docs/examples.md` for more details.

**API Changes:**
- `nflib.c` was not changed from an NF-developer standpoint, but it was modified to include a check for the `-F` flag, which indicates that a config file should be read to launch an NF.

**API Additions:**
 - `cJSON* onvm_config_parse_file(const char* filename)`: Reads a JSON config and stores the contents in a cJSON struct. For further reference on cJSON, see its [documentation](https://github.com/DaveGamble/cJSON).
- `int onvm_config_create_nf_arg_list(cJSON* config, int* argc, char** argv[])`: Given a cJSON struct and pointers to the original command line arguments, generate a new `argc` and `argv` using the config file values.

### Minor improvements

  - **Return packets in bulk**: Adds support for returning packets in bulk instead of one by one by using  `onvm_nflib_return_pkt_bulk`. Useful for functions that buffer a group of packets before returning them for processing or for NFs that create batches of packets in the fast path. *No breaking API changes.*
  - **Updated `corehelper.py` script**: Fixed the `scripts/corehelper.py` file so that it correctly reports recommended core usage instructions. The script assumes a single CPU socket system and verifies that hyperthreading is disabled.
  - **Adjusted default number of TX queues**: Previously, the ONVM manager always started `MAX_NFS` transmit queues on each NIC port. This is unnecessary and causes a problem with SR-IOV and NICs with limited queue support. Now the manager creates one queue per TX thread.
  - Bug fixes were made to [prevent a crash](https://github.com/sdnfv/openNetVM/commit/087891d9fea3b3ab011254dd405ef9e708d2e43d) of `speed_tester` during allocation of packets when there are no free mbufs and to [fix an invalid path](https://github.com/sdnfv/openNetVM/commit/a7978304914670ae9dfd2e3571af21ec7ed29013) causing an error when attempting to use Pktgen with the `run-pktgen.sh` script. Additionally, a few [minor documentation edits](https://github.com/sdnfv/openNetVM/commit/6005be5724552cda3f84b84e39cdc7bee846194c) were made.


## v18.05 (5/31/18): Bug Fixes, Latency Measurements, and Docker Image
This release adds a feature to the Speed Tester example NF to support latency measurements by using the `-l` flag. Latency is calculated by writing a timestamp into the packet body and comparing this value when the packet is returned to the Speed Tester NF. A sample use case is to run 3 speed tester NFs configured to send in a chain, with the last NF sending back to the first. The first NF can use the `-l` flag to measure latency for this chain. Note that only one NF in a chain should be using the flag since otherwise timestamp information written to the packet will conflict.

It also makes minor changes to the setup scripts to work better in NSF CloudLab environments.

We now provide a docker container image that can be used to easily run NFs inside containers. See the [Docker Docs](./Docker.md) for more information.

OpenNetVM support has now been integrated into the mainline [mTCP repository](https://github.com/eunyoung14/mtcp).

Finally, we are now adding issues to the GitHub Issue Tracker with the [Good First Issue](https://github.com/sdnfv/openNetVM/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22) label to help others find ways to contribute to the project. Please take a look and contribute a pull request!

An NSF CloudLab template including OpenNetVM 18.05, mTCP, and some basic networking utilities is available here: https://www.cloudlab.us/p/GWCloudLab/onvm-18.05

*No API changes were introduced in this release.*

## v18.03 (3/27/18): Updated DPDK and preliminary mTCP support
This release updates the DPDK submodule to use version 17.08.  This DPDK update caused breaking changes to its API, so updates have been made to the OpenNetVM manager and example NFs to support this change.

In order to update to the latest version of DPDK you must run:

```
git submodule update --init
```

And then rebuild DPDK using the [install guide](./Install.md) or running these commands:

```
cd dpdk
make clean
make config T=$RTE_TARGET
make T=$RTE_TARGET -j 8
make install T=$RTE_TARGET -j 8
```
(you may need to install the `libnuma-dev` package if you get compilation errors)

This update also includes preliminary support for mTCP-based endpoint NFs. Our OpenNetVM driver has been merged into the [develop branch of mTCP](https://github.com/eunyoung14/mtcp/tree/devel). This allows you to run services like high performance web servers on an integrated platform with other middleboxes.  See the mTCP repository for usage instructions.

Other changes include:
 - Adds a new "Router NF" example which can be used to redirect packets to specific NFs based on their IP. This is currently designed for simple scenarios where a small number of IPs are matched to NFs acting as connection terminating endpoints (e.g., mTCP-based servers).
 - Bug Fix in ARP NF to properly handle replies based on the ARP OP code.
 - Updated pktgen submodule to 3.49 which works with DPDK 17.08.

 An NSF CloudLab template including OpenNetVM 18.03, mTCP, and some basic networking utilities is available here: https://www.cloudlab.us/p/GWCloudLab/onvm-18.03

*No API changes were introduced in this release.*

## v18.1 (1/31/18): Bug Fixes and Speed Tester improvements
This release includes several bug fixes including:
 - Changed macro and inline function declarations to improve compatibility with 3rd party libraries and newer gcc versions (tested with 4.8 and 5.4)
 - Solved memory leak in SDN flow table example
 - Load Balancer NF now correctly updates MAC address on outgoing packets to backend servers

Improvements:
 - Speed Tester NF now supports a `-c` argument indicating how many packets should be created. If combined with the PCAP replay flag, this parameter controls how many of packets in the trace will be transmitted. A larger packet count may be required when trying to use Speed Tester to saturate a chain of network functions.

*No API changes were introduced in this release.*

## v17.11 (11/16/17): New TX thread architecture, realistic NF examples, better stats, messaging, and more
Since the last official release there have been substantial changes to openNetVM, including the switch to date based versioning mentioned above. Changes include:
 - New TX architecture: previously NFs enqueued packets into a TX ring that was read by TX threads in the manager, which consumed significant CPU resources.
 By moving TX thread logic to the NF side, ONVM can run with fewer cores, improving efficiency.  NFs can then directly pass packets which saves enqueueing/dequeuing to an extra ring. TX threads still send packets out the NIC, but NFs primarily do packet passing--it is suggested to run the system with at least 1 TX thread to handle outgoing packets. Despite these changes, TX threads can still perform the same work that they did before. If a user would like to run ONVM with TX threads handling all packet passing, they must set `NF_HANDLE_TX` to `0` in `onvm_common.h`
   - Our tests show this change increases NF transmit speed from 20 Mpps to 41 Mpps with the Speed Tester NF benchmark, while consuming fewer cores.
 - New NFs: we have developed several new sample NFs, including:
   - `examples/ndpi_stats` uses the [nDPI library](https://github.com/ntop/nDPI) for deep packet inspection to determine the protocol of each flow.
   - `examples/flow_tracker` illustrates how to use ONVM's flow table library to track the list of open connections and print information about them.
   - `examples/arp_response` can be used to assign an IP to the NICs managed by openNetVM. The NF is capable of responding to ARP requests. This facilitates NFs that act as connection endpoints, load balancers, etc.
   - `examples/load_balancer` is a layer 3, round-robin load balancer. When a packet arrives the NF checks whether it is from an already existing flow. If not, it creates a new flow entry and assigns it to a destination backend server. This NF uses ARP support to assign an accessible IP to the openNetVM host running the load balancer.
   - [Snort NF](https://github.com/sdnfv/onvm-snort) provides a version of the Snort intrusion detection system ported to openNetVM.
 - [PCAP replay](https://github.com/sdnfv/openNetVM/commit/4b40bdca5117c6a72f57dfa5c622173abfc49483): the Speed Tester NF can now load a packet trace file and use that to generate the packets that it transmits.
 - [NF idle call back](https://github.com/sdnfv/openNetVM/commit/d4bc32aeffeb5f2082cfb978b3860a407c962a93): Traditionally, NFs would wait until the ONVM manager puts packets on their Rx buffer and then calls their packet handler function to process them.  This meant that NFs would sit idle until they have some packets to process.  With this change, NFs can now run at any time even if there are no packets to process.  NFs can provide a callback handler function to be registered with NFLib.  Once this callback handler is registered with NFLib, the function will be run constantly even if there are no packets to be processed.
 - [Web-based stats](https://github.com/sdnfv/openNetVM/commit/b7380020837dcecc32b3fb72e79190c256670e80): the ONVM manager can now display statistics about the active NFs. See `onvm_web/` for more information.
 - [NF--Manager Messaging Interface](https://github.com/sdnfv/openNetVM/commit/125e6dd5e9339b5492723866988edf05ecadcd48): We have expanded the interface between the manager and NFs to allow more flexible message passing.
 - A multitude of other bug fixes, documentation improvements, etc!

## v1.1.0 (1/25/17): Refactoring to library, new NFs
This release refactored the code into a proper library, making it easier to include with more advanced NFs. We also added new AES encryption and decryption NFs that operate on UDP packets.

## v1.0.0 (8/25/16): Refactoring to improve code organization
A big set of commits to clean the structure and simplify onvm source code.
We separated all functions into the main.c of the manager into modules :
 - `onvm_stats` : functions displaying statistics
 - `onvm_pkt` : functions related to packet processing
 - `onvm_nf` : functions related to NFs management.

Each module comes with a header file with commented prototypes. And each c and h file has been "cut" into parts :
 - interfaces, or functions called outside of the module
 - internal functions, the functions called only inside the module and doing all the work
 - helper functions, simple and short functions used many times through the module.

**API Changes:**
 - NFs now need to call functions like `onvm_nflib_*` instead of `onvm_nf_*`.  For example, `onvm_nflib_init` instead of `onvm_nf_init`.  The example NFs have all been updated accordingly.
 - NF `Makefiles` need to be updated to find the path to `onvm_nflib`.


## 4/24/16: Initial Release
Initial source code release.



[firewall_nf_readme]: ../examples/firewall/README.md
[payload_scan_nf_readme]: ../examples/payload_scan/README.md
[shared_core_docs]: ./NF_Dev.md#shared-cpu-mode
[nfvnice_branch]: https://github.com/sdnfv/openNetVM/tree/experimental/nfvnice-reinforce
[flurries_paper]: https://dl.acm.org/citation.cfm?id=2999602
[nfvnice_paper]: https://dl.acm.org/citation.cfm?id=3098828

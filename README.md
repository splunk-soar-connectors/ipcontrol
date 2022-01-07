[comment]: # "Auto-generated SOAR connector documentation"
# IP Control

Publisher: Splunk Community  
Connector Version: 1\.0\.10  
Product Vendor: BT Diamond  
Product Name: IP Control  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 5\.0\.0  

Provides access to IP Control API's

### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a IP Control asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**base\_url** |  required  | string | IP or Hostname for IP Control
**username** |  required  | string | Username for IP Control
**password** |  required  | password | Password

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration  
[get block type](#action-get-block-type) - Returns block type for endpoint using IP or Hostname  
[get ip address](#action-get-ip-address) - Gets Hostname associated with known IP Address  
[get child block](#action-get-child-block) - Gets Child Block  
[get hostname](#action-get-hostname) - Gets the hostname from the known IP Address  

## action: 'test connectivity'
Validate the asset configuration for connectivity using supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'get block type'
Returns block type for endpoint using IP or Hostname

Type: **investigate**  
Read only: **True**

Returns the block type for an endpoint using the IP Address or the Hostname\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**ip\_address** |  optional  | IP Address | string |  `ip` 
**hostname** |  optional  | Hostname | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.hostname | string | 
action\_result\.parameter\.ip\_address | string |  `ip` 
action\_result\.data\.\*\.\*\.blockType | string | 
action\_result\.data\.\*\.\*\.childBlock\.SWIPname | string | 
action\_result\.data\.\*\.\*\.childBlock\.blockAddr | string |  `ip` 
action\_result\.data\.\*\.\*\.childBlock\.blockName | string | 
action\_result\.data\.\*\.\*\.childBlock\.blockSize | string | 
action\_result\.data\.\*\.\*\.childBlock\.blockStatus | string | 
action\_result\.data\.\*\.\*\.childBlock\.blockType | string | 
action\_result\.data\.\*\.\*\.childBlock\.container | string | 
action\_result\.data\.\*\.\*\.childBlock\.createDate | string | 
action\_result\.data\.\*\.\*\.childBlock\.createReverseDomains | string |  `domain` 
action\_result\.data\.\*\.\*\.childBlock\.description | string | 
action\_result\.data\.\*\.\*\.childBlock\.discoveryAgent | string | 
action\_result\.data\.\*\.\*\.childBlock\.domainType | string |  `domain` 
action\_result\.data\.\*\.\*\.childBlock\.excludeFromDiscovery | string | 
action\_result\.data\.\*\.\*\.childBlock\.interfaceAddress | string |  `ip` 
action\_result\.data\.\*\.\*\.childBlock\.interfaceName | string | 
action\_result\.data\.\*\.\*\.childBlock\.ipv6 | boolean | 
action\_result\.data\.\*\.\*\.childBlock\.lastUpdateDate | string | 
action\_result\.data\.\*\.\*\.childBlock\.nonBroadcast | boolean | 
action\_result\.data\.\*\.\*\.childBlock\.primarySubnet | boolean | 
action\_result\.data\.\*\.\*\.childBlock\.vrfName | string | 
action\_result\.data\.\*\.\*\.subnetPolicy\.cascadePrimaryDhcpServer | boolean | 
action\_result\.summary | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get ip address'
Gets Hostname associated with known IP Address

Type: **investigate**  
Read only: **True**

Gets Hostname associated with known IP Address\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**hostname** |  required  | Hostname | string |  `hostname` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.hostname | string |  `hostname` 
action\_result\.data\.\*\.addressType | string | 
action\_result\.data\.\*\.container | string | 
action\_result\.data\.\*\.description | string | 
action\_result\.data\.\*\.deviceType | string | 
action\_result\.data\.\*\.duid | string | 
action\_result\.data\.\*\.hostname | string |  `host name` 
action\_result\.data\.\*\.id | numeric | 
action\_result\.data\.\*\.interfaces\.\*\.container | string | 
action\_result\.data\.\*\.interfaces\.\*\.id | numeric | 
action\_result\.data\.\*\.interfaces\.\*\.ipAddress | string |  `ip` 
action\_result\.data\.\*\.interfaces\.\*\.name | string | 
action\_result\.data\.\*\.interfaces\.\*\.relayAgentCircuitId | string | 
action\_result\.data\.\*\.interfaces\.\*\.relayAgentRemoteId | string | 
action\_result\.data\.\*\.interfaces\.\*\.sequence | numeric | 
action\_result\.data\.\*\.interfaces\.\*\.virtual | boolean | 
action\_result\.data\.\*\.ipAddress | string |  `ip` 
action\_result\.summary | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get child block'
Gets Child Block

Type: **investigate**  
Read only: **True**

Gets the Child block\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**name** |  optional  | The name of the block to export\. Ex\. name='My Block' | string | 
**block** |  optional  | The CIDR notation of the block to export\. The accepted format for CIDR notation is 'block\_address/block\_size'\. Ex\. block='10\.0\.0\.0/24' | string | 
**block\_type** |  optional  | The block type name of the block\(s\) to export\. Ex\. blocktype='private' | string | 
**container** |  optional  | The container name of the block\(s\) to be exported\. Ex\. container='Exton' | string | 
**create\_date** |  optional  | The GMT date and time the block was created | string | 
**last\_update** |  optional  | The GMT date and time the block was last updated | string | 
**parent\_container** |  optional  | Only applied when parentBlock is supplied\. Specifies the name of the parent block's container\. Useful in order to eliminate ambiguity by specifying the container name, fully qualified or not | string | 
**status** |  optional  | The status of the block\(s\) to be exported\. Valid options are\: free, aggregate, reserved, subnet, fullyassigned | string | 
**ip\_version** |  optional  | The IP Version of the block\(s\) to be exported\. Valid options are\: v4 and v6 | string | 
**udf** |  optional  | The name and value of a UDF attached to the block\(s\) to be exported | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.block | string | 
action\_result\.parameter\.block\_type | string | 
action\_result\.parameter\.container | string | 
action\_result\.parameter\.create\_date | string | 
action\_result\.parameter\.ip\_version | string | 
action\_result\.parameter\.last\_update | string | 
action\_result\.parameter\.name | string | 
action\_result\.parameter\.parent\_container | string | 
action\_result\.parameter\.status | string | 
action\_result\.parameter\.udf | string | 
action\_result\.data\.\*\.\*\.childBlock\.SWIPname | string | 
action\_result\.data\.\*\.\*\.childBlock\.allocationReason | string | 
action\_result\.data\.\*\.\*\.childBlock\.blockAddr | string |  `ip` 
action\_result\.data\.\*\.\*\.childBlock\.blockName | string | 
action\_result\.data\.\*\.\*\.childBlock\.blockSize | string | 
action\_result\.data\.\*\.\*\.childBlock\.blockStatus | string | 
action\_result\.data\.\*\.\*\.childBlock\.blockType | string | 
action\_result\.data\.\*\.\*\.childBlock\.container | string | 
action\_result\.data\.\*\.\*\.childBlock\.createDate | string | 
action\_result\.data\.\*\.\*\.childBlock\.createReverseDomains | string |  `domain` 
action\_result\.data\.\*\.\*\.childBlock\.description | string | 
action\_result\.data\.\*\.\*\.childBlock\.discoveryAgent | string | 
action\_result\.data\.\*\.\*\.childBlock\.domainType | string |  `domain` 
action\_result\.data\.\*\.\*\.childBlock\.excludeFromDiscovery | string | 
action\_result\.data\.\*\.\*\.childBlock\.interfaceAddress | string |  `ip` 
action\_result\.data\.\*\.\*\.childBlock\.interfaceName | string | 
action\_result\.data\.\*\.\*\.childBlock\.ipv6 | boolean | 
action\_result\.data\.\*\.\*\.childBlock\.lastUpdateDate | string | 
action\_result\.data\.\*\.\*\.childBlock\.nonBroadcast | boolean | 
action\_result\.data\.\*\.\*\.childBlock\.primarySubnet | boolean | 
action\_result\.data\.\*\.\*\.childBlock\.vrfName | string | 
action\_result\.data\.\*\.\*\.subnetPolicy\.cascadePrimaryDhcpServer | boolean | 
action\_result\.data\.\*\.\*\.subnetPolicy\.forwardDomainTypes | string | 
action\_result\.data\.\*\.\*\.subnetPolicy\.forwardDomains | string | 
action\_result\.data\.\*\.\*\.subnetPolicy\.networkLink | string | 
action\_result\.summary | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get hostname'
Gets the hostname from the known IP Address

Type: **investigate**  
Read only: **True**

Gets the Hostname related to a known IP Address\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**ip\_address** |  required  | IP Address | string |  `ip` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.ip\_address | string |  `ip` 
action\_result\.data\.\*\.addressType | string | 
action\_result\.data\.\*\.container | string | 
action\_result\.data\.\*\.description | string | 
action\_result\.data\.\*\.deviceType | string | 
action\_result\.data\.\*\.duid | string | 
action\_result\.data\.\*\.hostname | string |  `host name` 
action\_result\.data\.\*\.id | numeric | 
action\_result\.data\.\*\.interfaces\.\*\.container | string | 
action\_result\.data\.\*\.interfaces\.\*\.id | numeric | 
action\_result\.data\.\*\.interfaces\.\*\.ipAddress | string |  `ip` 
action\_result\.data\.\*\.interfaces\.\*\.name | string | 
action\_result\.data\.\*\.interfaces\.\*\.relayAgentCircuitId | string | 
action\_result\.data\.\*\.interfaces\.\*\.relayAgentRemoteId | string | 
action\_result\.data\.\*\.interfaces\.\*\.sequence | numeric | 
action\_result\.data\.\*\.interfaces\.\*\.virtual | boolean | 
action\_result\.data\.\*\.ipAddress | string |  `ip` 
action\_result\.summary | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 

```
[training@localhost training_materials]$ sqoop eval --connect jdbc:mysql://localhost/loudacre --username training --password training --query "describe accounts"                                                                                                       
```
19/03/11 01:27:19 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0                                                           
19/03/11 01:27:19 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.        
19/03/11 01:27:20 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.                                          
---------------------------------------------------------------------------------------------------------                           
| Field                | Type                 | Null | Key | Default              | Extra                |                          
---------------------------------------------------------------------------------------------------------                           
| acct_num             | int(11)              | NO  | PRI | (null)               |                      |                           
| acct_create_dt       | datetime             | NO  |     | (null)               |                      |                           
| acct_close_dt        | datetime             | YES |     | (null)               |                      |                           
| first_name           | varchar(255)         | NO  |     | (null)               |                      |                           
| last_name            | varchar(255)         | NO  |     | (null)               |                      |                           
| address              | varchar(255)         | NO  |     | (null)               |                      |                           
| city                 | varchar(255)         | NO  |     | (null)               |                      |                           
| state                | varchar(255)         | NO  |     | (null)               |                      |                           
| zipcode              | varchar(255)         | NO  |     | (null)               |                      |                           
| phone_number         | varchar(255)         | NO  |     | (null)               |                      |                           
| created              | datetime             | NO  |     | (null)               |                      |                           
| modified             | datetime             | NO  |     | (null)               |                      |                           
---------------------------------------------------------------------------------------------------------                           
```
[training@localhost training_materials]$ sqoop import \                                                                             
> --connect jdbc:mysql://localhost/loudacre \                                                                                       
> --username training --password training \                                                                                         
> --table accounts \                                                                                                                
> --columns "acct_num, first_name, last_name" \                                                                                     
> --fields-terminated-by "\t" \                                                                                                     
> --target-dir /loudacre/accounts/user_info \                                                                                       
> --as-textfile
```
19/03/11 01:27:29 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/03/11 01:27:29 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/03/11 01:27:29 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
19/03/11 01:27:29 INFO tool.CodeGenTool: Beginning code generation
19/03/11 01:27:30 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/03/11 01:27:30 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/03/11 01:27:30 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce
Note: /tmp/sqoop-training/compile/bf4fb1923efe60548e5f31b8db58c602/accounts.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
19/03/11 01:27:32 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/bf4fb1923efe60548e5f31b8db58c602/accounts.jar
19/03/11 01:27:32 WARN manager.MySQLManager: It looks like you are importing from mysql.
19/03/11 01:27:32 WARN manager.MySQLManager: This transfer can be faster! Use the --direct
19/03/11 01:27:32 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.
19/03/11 01:27:32 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
19/03/11 01:27:32 INFO mapreduce.ImportJobBase: Beginning import of accounts
19/03/11 01:27:32 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
19/03/11 01:27:32 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
19/03/11 01:27:33 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/03/11 01:27:33 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/03/11 01:27:36 INFO db.DBInputFormat: Using read commited transaction isolation
19/03/11 01:27:36 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts`
19/03/11 01:27:36 INFO db.IntegerSplitter: Split size: 32440; Num splits: 4 from: 1 to: 129761
19/03/11 01:27:36 INFO mapreduce.JobSubmitter: number of splits:4
19/03/11 01:27:36 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1552277367717_0009
19/03/11 01:27:36 INFO impl.YarnClientImpl: Submitted application application_1552277367717_0009
19/03/11 01:27:37 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1552277367717_0009/
19/03/11 01:27:37 INFO mapreduce.Job: Running job: job_1552277367717_0009
19/03/11 01:27:46 INFO mapreduce.Job: Job job_1552277367717_0009 running in uber mode : false
19/03/11 01:27:46 INFO mapreduce.Job:  map 0% reduce 0%
19/03/11 01:27:53 INFO mapreduce.Job:  map 25% reduce 0%
19/03/11 01:27:58 INFO mapreduce.Job:  map 50% reduce 0%
19/03/11 01:28:04 INFO mapreduce.Job:  map 75% reduce 0%
19/03/11 01:28:10 INFO mapreduce.Job:  map 100% reduce 0%
19/03/11 01:28:11 INFO mapreduce.Job: Job job_1552277367717_0009 completed successfully
19/03/11 01:28:11 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=560464
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=470
		HDFS: Number of bytes written=2615920
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters 
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=17798
		Total vcore-seconds taken by all map tasks=17798
		Total megabyte-seconds taken by all map tasks=4556288
	Map-Reduce Framework
		Map input records=129761
		Map output records=129761
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=251
		CPU time spent (ms)=4130
		Physical memory (bytes) snapshot=492138496
		Virtual memory (bytes) snapshot=8262045696
		Total committed heap usage (bytes)=251920384
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=2615920
19/03/11 01:28:11 INFO mapreduce.ImportJobBase: Transferred 2.4947 MB in 38.0858 seconds (67.0751 KB/sec)
19/03/11 01:28:11 INFO mapreduce.ImportJobBase: Retrieved 129761 records.
```
[training@localhost training_materials]$ sqoop import \
> --connect jdbc:mysql://localhost/loudacre \
> --username training --password training \
> --table accounts \
> --columns "acct_num, first_name, last_name" \
> --fields-terminated-by "\t" \
> --target-dir /loudacre/accounts/user_compressed \
> --as-parquetfile \
> --compression-codec \
> org.apache.hadoop.io.compress.SnappyCodec
```
19/03/11 01:28:34 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/03/11 01:28:34 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/03/11 01:28:34 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
19/03/11 01:28:34 INFO tool.CodeGenTool: Beginning code generation
19/03/11 01:28:34 INFO tool.CodeGenTool: Will generate java class as codegen_accounts
19/03/11 01:28:34 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/03/11 01:28:34 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/03/11 01:28:34 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce
Note: /tmp/sqoop-training/compile/b2fc510fa631a77259c90b37354679f1/codegen_accounts.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
19/03/11 01:28:37 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/b2fc510fa631a77259c90b37354679f1/codegen_accounts.jar
19/03/11 01:28:37 WARN manager.MySQLManager: It looks like you are importing from mysql.
19/03/11 01:28:37 WARN manager.MySQLManager: This transfer can be faster! Use the --direct
19/03/11 01:28:37 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.
19/03/11 01:28:37 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
19/03/11 01:28:37 INFO mapreduce.ImportJobBase: Beginning import of accounts
19/03/11 01:28:37 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
19/03/11 01:28:38 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
19/03/11 01:28:39 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/03/11 01:28:39 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/03/11 01:28:40 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/03/11 01:28:40 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/03/11 01:28:42 INFO db.DBInputFormat: Using read commited transaction isolation
19/03/11 01:28:42 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts`
19/03/11 01:28:42 INFO db.IntegerSplitter: Split size: 32440; Num splits: 4 from: 1 to: 129761
19/03/11 01:28:42 INFO mapreduce.JobSubmitter: number of splits:4
19/03/11 01:28:43 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1552277367717_0010
19/03/11 01:28:43 INFO impl.YarnClientImpl: Submitted application application_1552277367717_0010
19/03/11 01:28:43 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1552277367717_0010/
19/03/11 01:28:43 INFO mapreduce.Job: Running job: job_1552277367717_0010
19/03/11 01:28:54 INFO mapreduce.Job: Job job_1552277367717_0010 running in uber mode : false
19/03/11 01:28:54 INFO mapreduce.Job:  map 0% reduce 0%
19/03/11 01:29:03 INFO mapreduce.Job:  map 25% reduce 0%
19/03/11 01:29:11 INFO mapreduce.Job:  map 50% reduce 0%
19/03/11 01:29:18 INFO mapreduce.Job:  map 75% reduce 0%
19/03/11 01:29:26 INFO mapreduce.Job:  map 100% reduce 0%
19/03/11 01:29:27 INFO mapreduce.Job: Job job_1552277367717_0010 completed successfully
19/03/11 01:29:28 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=565908
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=25234
		HDFS: Number of bytes written=1305047
		HDFS: Number of read operations=272
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=40
	Job Counters 
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=26353
		Total vcore-seconds taken by all map tasks=26353
		Total megabyte-seconds taken by all map tasks=6746368
	Map-Reduce Framework
		Map input records=129761
		Map output records=129761
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=577
		CPU time spent (ms)=8660
		Physical memory (bytes) snapshot=606601216
		Virtual memory (bytes) snapshot=8296480768
		Total committed heap usage (bytes)=251920384
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=0
19/03/11 01:29:28 INFO mapreduce.ImportJobBase: Transferred 1.2446 MB in 47.3735 seconds (26.9024 KB/sec)
19/03/11 01:29:28 INFO mapreduce.ImportJobBase: Retrieved 129761 records.
```
[training@localhost training_materials]$ 
[training@localhost training_materials]$ sqoop import \                                                                             
> --connect jdbc:mysql://localhost/loudacre \                                                                                       
> --username training --password training \                                                                                         
> --table accounts \                                                                                                                
> --where "state = 'CA'" \                                                                                                          
> --fields-terminated-by "\t" \                                                                                                     
> --target-dir /loudacre/accounts/CA \                                                                                              
> --as-parquetfile \                                                                                                                
> --compress -z                                                                                                                     
```
19/03/11 01:31:08 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0                                                           
19/03/11 01:31:08 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.        
19/03/11 01:31:08 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.                                          
19/03/11 01:31:08 INFO tool.CodeGenTool: Beginning code generation                                                                  
19/03/11 01:31:08 INFO tool.CodeGenTool: Will generate java class as codegen_accounts                                               
19/03/11 01:31:08 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1                         
19/03/11 01:31:08 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1                         
19/03/11 01:31:08 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce                                      
Note: /tmp/sqoop-training/compile/8574de438fbbf874636ea513b9f46454/codegen_accounts.java uses or overrides a deprecated API.        
Note: Recompile with -Xlint:deprecation for details.                                                                                
19/03/11 01:31:11 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/8574de438fbbf874636ea513b9f46454/codegen_accounts.jar                                                                                                                      
19/03/11 01:31:11 WARN manager.MySQLManager: It looks like you are importing from mysql.                                            
19/03/11 01:31:11 WARN manager.MySQLManager: This transfer can be faster! Use the --direct                                          
19/03/11 01:31:11 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.                                         
19/03/11 01:31:11 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)                                
19/03/11 01:31:11 INFO mapreduce.ImportJobBase: Beginning import of accounts                                                        
19/03/11 01:31:11 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address       
19/03/11 01:31:12 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar                          
19/03/11 01:31:13 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/03/11 01:31:13 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/03/11 01:31:15 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/03/11 01:31:15 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/03/11 01:31:17 INFO db.DBInputFormat: Using read commited transaction isolation
19/03/11 01:31:17 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts` WHERE ( state = 'CA' )
19/03/11 01:31:17 INFO db.IntegerSplitter: Split size: 32439; Num splits: 4 from: 1 to: 129760
19/03/11 01:31:17 INFO mapreduce.JobSubmitter: number of splits:4
19/03/11 01:31:17 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1552277367717_0011
19/03/11 01:31:17 INFO impl.YarnClientImpl: Submitted application application_1552277367717_0011
19/03/11 01:31:17 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1552277367717_0011/
19/03/11 01:31:17 INFO mapreduce.Job: Running job: job_1552277367717_0011
19/03/11 01:31:27 INFO mapreduce.Job: Job job_1552277367717_0011 running in uber mode : false
19/03/11 01:31:27 INFO mapreduce.Job:  map 0% reduce 0%
19/03/11 01:31:38 INFO mapreduce.Job:  map 25% reduce 0%
19/03/11 01:31:48 INFO mapreduce.Job:  map 50% reduce 0%
19/03/11 01:31:58 INFO mapreduce.Job:  map 75% reduce 0%
19/03/11 01:32:07 INFO mapreduce.Job:  map 100% reduce 0%
19/03/11 01:32:07 INFO mapreduce.Job: Job job_1552277367717_0011 completed successfully
19/03/11 01:32:07 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=568988
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=65386
		HDFS: Number of bytes written=4212382
		HDFS: Number of read operations=272
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=40
	Job Counters 
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=33826
		Total vcore-seconds taken by all map tasks=33826
		Total megabyte-seconds taken by all map tasks=8659456
	Map-Reduce Framework
		Map input records=92416
		Map output records=92416
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=923
		CPU time spent (ms)=15030
		Physical memory (bytes) snapshot=737382400
		Virtual memory (bytes) snapshot=8296345600
		Total committed heap usage (bytes)=251920384
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=0
19/03/11 01:32:07 INFO mapreduce.ImportJobBase: Transferred 4.0172 MB in 52.7638 seconds (77.9635 KB/sec)
19/03/11 01:32:07 INFO mapreduce.ImportJobBase: Retrieved 92416 records.
[training@localhost training_materials]$ 

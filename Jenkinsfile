    String workspace = "C:/Windows/system32/config/systemprofile/AppData/Local/Jenkins/.jenkins/workspace"
	
	@Library('jenkinslib')
	def tools = new org.devops.tools()
	
	pipeline {
	         agent { node { label "master"
			               customWorkspace "${workspace}"
			              }
			       }
			parameters { string(name: 'DEPLOY',defaultValue:'staging',description:'')}
				   
			 options{
			        timestamps()
					skipDefaultCheckout()
					disableConcurrentBuilds()
					timeout(time:1,unit:'HOURS')
			 }
			 
			 stages {
			        stage("GetCode"){
					   steps{
					      timeout(time:5,unit:'MINUTES'){
						       script{
							       println('获取代码')
							   }}
					   }
					   }
					   
					   stage("Build"){
					   steps{
					      timeout(time:5,unit:'MINUTES'){
						       script{
							       println('构建应用')
							       
							       mvnHome = tool "m2"
							       println(mvnHome)
							      
							   }}
					   }
					   }
					   
					   stage("CodeScan"){
					   steps{
					      timeout(time:5,unit:'MINUTES'){
						       script{
							       println('扫描代码')
							       
							       tools.PrintMes("this is sharelibrary")
							   }}
					   }
					   }
			 
			 }
			 
			 post{
			      always{
				     script{
					     println("always")}}
						 
				  success{
				     script{
					     currentBuild.description += "\n 构建成功！"}}		 
						 
				  failure{
				     script{
					     currentBuild.description += "\n 构建失败！"}}

                  aborted{
				     script{
					     currentBuild.description += "\n 构建取消！"}}							 
						 }
			 }

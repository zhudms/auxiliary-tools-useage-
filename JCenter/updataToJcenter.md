 ./gradlew clean build bintrayUpload -PbintrayUser=zhudms -PbintrayKey=cbaf82b938f6e3229102dfe7095fb9c426578cc9 -PdryRun=false
 
 *UNIX 系统需要./  ;windows 系统不要加这两个符号*<br/>
 *-PdryRun=false,不加这句不会提交到 jcenter*<br/>
 
 ```
 publish {
    userOrg ='zhudms'//bintray.com用户名
    groupId ='zhudms.maven.SelfCommonLib'//jcenter上的路径(正常路径不需要加SelfCommonLib)
    artifactId = 'SelfLib'//项目名称
    publishVersion = '0.0.3'//版本号
    desc = 'this is a lib' //描述，不重要
    website = 'https://github.com/zhudms/MavenDemo'//网站，不重要；尽量模拟github上的地址，例如我这样的；当然你有地址最好了
}
 
 ```



在  build.gradle(lib) 的 开头添加*apply plugin: 'com.novoda.bintray-release'*
结尾添加 publish

添加 build.gradle(project) 的buildscript {
    dependencies {
        classpath 'com.android.tools.build:gradle:3.0.1'
        classpath 'com.novoda:bintray-release:+'
        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}


每个单独的 lib 最好都单独创建项目提交,不然只提交一个 lib 时还要屏蔽其他项目的 build.gradle 中的配置,会疯的

编译会生成.aar .jar 等文件,都在maven 仓库中,可以通过项目页面右上角地址访问<a href="https://dl.bintray.com/zhudms/maven">仓库</a>




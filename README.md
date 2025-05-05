# XiaoZhiMed
## 项目简介
硅谷小智（医疗版）是一套针对Java程序员的大模型应用项目（医疗人工智能客服系统），囊括LangChain4j+RAG+向量数据库+FunctionCalling的一整套完整清晰的模型对接流程。硅谷小智是一个训练有素的医疗顾问和一个医疗伴诊助手，它能够为用户回答一些医院就诊中的常规问题，也可以基于当前临床实践和研究，针对患者提出的特定健康问题，提供详细、准确且使用的医疗建议。若需要进一步检查或就医，它也可以作为伴诊助手回答用户就医流程中的相关问题。例如，智能分导诊根据患者的病情和就医需求，智能推荐合适的科室和医生。又如，智能挂号助手，实现智能的预约挂号、智能取消挂号等服务。

## 项目展示
<img width="957" alt="xiaozhi" src="https://github.com/user-attachments/assets/e3ee9999-b7c9-4077-924e-a786f1520153" />

## 部署步骤
- 用IDEA导入后端项目java-ai-langchain4j，等待依赖自动下载
- 找到resources下的application.properties文件，修改DASH_API_KEY（这个需要注册[阿里云](https://www.aliyun.com/)账号，点击大模型导航栏，再点击通义千问max，然后获取API_KEY，将API_KEY配置到系统环境变量中，环境变量名就叫DASH_SCOPE_API_KEY）
```
langchain4j.open-ai.chat-model.api-key=${DASH_SCOPE_API_KEY}
langchain4j.community.dashscope.chat-model.api-key=${DASH_SCOPE_API_KEY}
langchain4j.community.dashscope.streaming-chat-model.api-key=${DASH_SCOPE_API_KEY}
langchain4j.community.dashscope.embedding-model.api-key=${DASH_SCOPE_API_KEY}
```
- 找到resources下的application.properties文件，配置MySQL数据库，确保username和password是你自己的MySQL账号密码。
```
spring.datasource.url=jdbc:mysql://localhost:3306/guiguxiaozhi?useUnicode=true&characterEncoding=UTF-8&serverTimezone=Asia/Shanghai&useSSL=false
spring.datasource.username=root
spring.datasource.password=123456
```
- MongoDB聊天记忆存储，安装MongoDB并启动服务（默认端口为27017）
```
spring.data.mongodb.uri=mongodb://localhost:27017/chat_memory_db
```
- 将knowledge压缩包放在没有中文的路径下，并解压
- 配置Pinecone的环境变量，[官网](https://www.pinecone.io/)注册并登录（科学上网）,获取API_KEY并配置为环境变量，变量名为PINECONE_API_KEY
- 安装Node.js（node-v18.17.1-x64.msi）
- 配置npm镜像，打开cmd 执行`npm config set registry https://registry.npmmirror.com`
- 进入项目目录（xiaozhi-ui放在一个无中文的路径下，并用cmd打开）执行下面的命令启动前端项目
```
cd xiaozhi-ui
npm i
npm run dev
```
- 找到项目中的XiaozhiApp，右键运行，然后浏览器打开[http://localhost:5173/](http://localhost:5173/)，即可对话。

## 参考资料
本项目是尚硅谷的[小智医疗项目](https://www.bilibili.com/video/BV1cpLTz1EVp?spm_id_from=333.788.videopod.episodes&vd_source=9a3b398e8389e2adc240e2a49c27a6c6)的源码，若需要更详细的了解，请移步B站看环环老师的讲解视频。

# 🚀 Jenkins CI Pipeline for Maven Project

This guide explains how to set up a Jenkins pipeline to automatically build a Maven project using GitHub as the source code repository.

---

## 🧩 Prerequisites

Make sure you have the following installed and configured:

- **Java (JDK 17 or later)**
- **Maven (Apache Maven 3.9+)**
- **Jenkins (LTS version preferred)**
- **Git**

---

## ⚙️ Step 1: Verify Java Installation

Check if Java is installed:

```bash
java -version
```

If not installed, download and install [Java JDK](https://www.oracle.com/java/technologies/javase-downloads.html).

---

## 🧱 Step 2: Install Maven and Configure Path

1. Download Maven from the [official site](https://maven.apache.org/download.cgi).

2. Extract it and note the path, e.g.:

   ```
   C:\Program Files\Apache\maven-3.9.9
   ```

3. Add Maven to **Environment Variables**:

   - `MAVEN_HOME` → `C:\Program Files\Apache\maven-3.9.9`
   - Add `%MAVEN_HOME%\bin` to the `Path`.

4. Verify installation:

   ```bash
   mvn -version
   ```

---

## 🧰 Step 3: Start Jenkins

If Jenkins is already installed, start it using:

```bash
net start jenkins
```

Or manually open the Jenkins Dashboard:

```
http://localhost:8080
```

Login with your credentials (default user: `admin`).

---

## 🧾 Step 4: Create a New Maven Job

1. Click **New Item** → Select **Maven Project** → Click **OK**.
2. In **Source Code Management**, select **Git** and enter your repository URL:

   ```
   https://github.com/rishi08083/Task8.git
   ```

3. Choose the branch:

   ```
   main
   ```

4. In **Build** section, specify Maven goals:

   ```
   clean install
   ```

5. Click **Save**.

---

## ⚡ Step 5: Build the Project

1. Click **Build Now**.
2. Jenkins will clone the repo, execute Maven build, and show logs under **Console Output**.

✅ Successful output example:

```
[INFO] BUILD SUCCESS
```

If no new commits are found:

```
No changes.
```

---

## 🔁 Step 6: (Optional) Add GitHub Webhook

To trigger builds automatically on every push:

1. Go to your GitHub repo → **Settings → Webhooks → Add webhook**
2. Payload URL:

   ```
   http://<your-public-ip>:8080/github-webhook/
   ```

3. Content type: `application/json`
4. Select **Just the push event** → Click **Add webhook**.

---

## 🧩 Step 7: Verify Build

Check build history in Jenkins:

- Green icon → ✅ Successful build
- Red icon → ❌ Failed build

Click on a build to view detailed logs and artifacts.

---

## 🎯 Result

You now have a fully working Jenkins CI pipeline that:

- Pulls source code from GitHub
- Builds it using Maven
- Displays real-time logs
- Can be extended to include test execution or deployment

---

## 🧠 Author

**Rishi Shori**

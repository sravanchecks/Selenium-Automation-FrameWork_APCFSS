# 🤖 Selenium Automation Framework - APCFSS

> A professional, production-ready test automation framework for web application testing

## 🎯 Quick Overview

This is a **comprehensive Selenium WebDriver automation framework** built to streamline web UI testing with industry best practices including the Page Object Model (POM), data-driven testing, and parallel execution capabilities.

**Perfect for:** QA engineers and test automation specialists looking for a scalable testing solution.

---

## ⚡ Key Highlights

- ✅ **Page Object Model (POM)** - Clean, maintainable code structure
- ✅ **Data-Driven Testing** - Parameterized test execution
- ✅ **Cross-Browser Support** - Chrome, Firefox, Safari, Edge
- ✅ **Parallel Execution** - Run tests simultaneously for faster feedback
- ✅ **Comprehensive Reporting** - HTML & Allure reports included
- ✅ **Robust Logging** - Full execution logs for debugging
- ✅ **Environment Management** - Easy switching between dev/staging/prod

---

## 📋 Table of Contents

- [Quick Overview](#quick-overview)
- [Key Highlights](#key-highlights)
- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [Installation & Setup](#installation--setup)
- [Configuration](#configuration)
- [Running Tests](#running-tests)
- [Test Examples](#test-examples)
- [Reports & Logs](#reports--logs)
- [Contributing](#contributing)

---

## 📦 Prerequisites

| Requirement | Version |
|---|---|
| Java | 11+ |
| Selenium WebDriver | 4.x |
| Maven | 3.6+ |
| TestNG | 7.0+ |
| Chrome/Firefox/Edge | Latest |

---

## 📁 Project Structure

```
Selenium-Automation-FrameWork_APCFSS/
├── src/
│   ├── main/
│   │   ├── java/framework/
│   │   │   ├── pages/           # Page Object classes
│   │   │   ├── tests/           # Test classes
│   │   │   ├── utils/           # Utility methods
│   │   │   └── config/          # Configuration
│   │   └── resources/
│   │       ├── config.properties
│   │       └── testdata/
│   └── test/java/
├── reports/                     # Test reports
├── logs/                        # Execution logs
├── pom.xml
└── README.md
```

---

## 🚀 Installation & Setup

### 1. Clone Repository
```bash
git clone https://github.com/sravanchecks/Selenium-Automation-FrameWork_APCFSS.git
cd Selenium-Automation-FrameWork_APCFSS
```

### 2. Install Dependencies
```bash
mvn clean install
```

### 3. Verify Setup
```bash
mvn -v
java -version
```

---

## ⚙️ Configuration

Edit `src/main/resources/config.properties`:

```properties
# Browser Settings
browser=chrome
headless_mode=false
window_size=1920,1080

# Application URL
base_url=https://your-application.com

# Timeouts (seconds)
implicit_wait=10
explicit_wait=15
page_load_timeout=30

# Logging
log_level=INFO
```

---

## 🧪 Running Tests

```bash
# Run all tests
mvn test

# Run specific test class
mvn test -Dtest=LoginTest

# Run in headless mode
mvn test -Dheadless=true

# Generate Allure report
mvn allure:report
```

---

## 💡 Test Examples

### Example 1: Login Test
```java
public class LoginPageTest {
    private WebDriver driver;
    private LoginPage loginPage;

    @BeforeTest
    public void setup() {
        driver = new ChromeDriver();
        loginPage = new LoginPage(driver);
    }

    @Test
    public void testSuccessfulLogin() {
        loginPage.navigateTo()
                 .enterUsername("user@test.com")
                 .enterPassword("password123")
                 .clickLoginButton();
        
        Assert.assertTrue(loginPage.isUserLoggedIn());
    }

    @AfterTest
    public void tearDown() {
        driver.quit();
    }
}
```

### Example 2: Page Object Class
```java
public class LoginPage {
    private WebDriver driver;
    
    // Locators
    private By usernameField = By.id("username");
    private By passwordField = By.id("password");
    private By loginButton = By.xpath("//button[contains(text(), 'Login')]");

    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }

    public LoginPage navigateTo() {
        driver.get("https://your-application.com/login");
        return this;
    }

    public LoginPage enterUsername(String username) {
        driver.findElement(usernameField).sendKeys(username);
        return this;
    }

    public LoginPage enterPassword(String password) {
        driver.findElement(passwordField).sendKeys(password);
        return this;
    }

    public void clickLoginButton() {
        driver.findElement(loginButton).click();
    }

    public boolean isUserLoggedIn() {
        return driver.findElement(By.xpath("//span[@class='user-profile']")).isDisplayed();
    }
}
```

---

## 📊 Reports & Logs

- **Test Reports**: `target/surefire-reports/`
- **Allure Reports**: `target/allure-results/`
- **Logs**: `logs/automation.log`

View Allure report:
```bash
mvn allure:serve
```

---

## 🤝 Contributing

1. Fork the repository
2. Create feature branch: `git checkout -b feature/your-feature`
3. Commit changes: `git commit -m 'Add feature'`
4. Push to branch: `git push origin feature/your-feature`
5. Create Pull Request

---

## 📧 Contact & Support

- **Author**: sravanchecks
- **GitHub**: [sravanchecks](https://github.com/sravanchecks)
- **Repository**: [Selenium-Automation-FrameWork_APCFSS](https://github.com/sravanchecks/Selenium-Automation-FrameWork_APCFSS)

---

**Last Updated**: May 2026 | **Version**: 1.0.0


      
  const fetch = require('node-fetch');

exports.handler = async (event) => {
  const { prompt } = JSON.parse(event.body);  // 여전히 body는 JSON으로 전달되어야 함

  const apiKey = process.env.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;

  // GPT API에 POST 요청 보내기
  const res = await fetch("https://api.openai.com/v1/chat/completions", {
    method: "POST",
    headers: {
      "Authorization": `Bearer ${apiKey}`,
      "Content-Type": "application/json"  // 반드시 JSON 헤더가 필요함
    },
    body: JSON.stringify({
      model: "gpt-3.5-turbo",
      messages: [{ role: "user", content: prompt }]
    })
  });

  const data = await res.json();
  return {
    statusCode: 200,
    body: JSON.stringify({ reply: data.choices[0].message.content })
  };
};
